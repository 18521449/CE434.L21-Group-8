## **Setup Environment**
- Create Github Repository
- [Install Ubuntu Desktop](https://ubuntu.com/download/desktop/thank-you?version=20.04.2.0&architecture=amd64)
- Install Python 3.6 or later
```shell
sudo apt-get install python3
sudo apt-get install python3-pip3
```
- Install OpenCV for Python
```shell
sudo apt-get install python3-opencv
```
- [Install Vivado](https://www.xilinx.com/support/download.html)
- [Install Modelsim](https://fpgasoftware.intel.com/?product=modelsim_ae#tabs-2)
## **Write a "Hello world" app**
```python
import cv2

# Open a video stream from laptop's built-in webcam
cap = cv2.VideoCapture(0)
if cap.isOpened() == False:
    print('Failed to open webcam')

# Get the stream's dimensions
width  = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))

# Define the codec and a VideoWriter object (30 fps)
fourcc = cv2.VideoWriter_fourcc(*'xvid')
out = cv2.VideoWriter('webcam_output.avi', fourcc, 30.0, (width, height))

while cap.isOpened():
    ret, frame = cap.read()

    if ret == False:
        break
    else:
        # Output the frame to the video
        out.write(frame)

        # Show the frame on the screen
        cv2.imshow('Webcam', frame)

        # Wait for 'q' to stop the stream
        if cv2.waitKey(1) & 0xff == ord('q'):
            break

# Close the window
cap.release()
cv2.destroyAllWindows()

# Release the output
out.release()
```
