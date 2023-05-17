# live-web-cam-face_detect
Script to recognise faces on a live webcam feed

This is a Python script that uses the face_recognition library and OpenCV to perform real-time face recognition from a video stream. Let's go through the code step by step:

1. The necessary libraries and modules are imported: `face_recognition`, `imutils`, `pickle`, `time`, and `cv2` (OpenCV).

2. The path to the XML file containing the pre-trained cascade classifier for face detection is specified using the `cv2.CascadeClassifier` class. This classifier is used to detect faces in each frame of the video stream.

3. The previously saved known faces and their corresponding embeddings are loaded using the `pickle` module and stored in the `data` variable.

4. The script initializes the video capture using `cv2.VideoCapture(0)`, which captures video from the default camera (index 0). You can change the index or specify a video file to read from.

5. The main loop starts, where each frame from the video stream is processed.

6. The frame is read using `video_capture.read()`, and then converted to grayscale using `cv2.cvtColor()`.

7. The `faceCascade.detectMultiScale()` function is used to detect faces in the grayscale frame. It returns a list of rectangles representing the bounding boxes of the detected faces.

8. The frame is converted from BGR to RGB using `cv2.cvtColor()` because the face_recognition library expects RGB images.

9. Face encodings are computed for each face detected in the frame using `face_recognition.face_encodings()`. These encodings represent the unique features of each face.

10. The script compares the computed encodings with the encodings of known faces stored in `data["encodings"]`. It uses `face_recognition.compare_faces()` to obtain an array of boolean values indicating whether a face in the frame matches closely with any known face.

11. If a match is found (True in `matches`), the script determines the name of the matched face by finding the corresponding index in `data["names"]` and using the associated name.

12. To handle cases where multiple faces in the frame match known faces closely, the script keeps count of each recognized face using a dictionary. It selects the name with the highest count as the final recognized name.

13. The recognized names are appended to the `names` list.

14. The script iterates over the detected faces and recognized names, drawing rectangles around the faces and displaying the corresponding names on the frame using `cv2.rectangle()` and `cv2.putText()`.

15. The frame with the overlays is displayed using `cv2.imshow()`.

16. The script waits for the 'q' key to be pressed to break out of the loop and stop the program.

17. Finally, the video capture is released and all windows are closed using `video_capture.release()` and `cv2.destroyAllWindows()`.

This script allows you to perform real-time face recognition using a pre-trained model and a video stream from a camera or a video file. It can be useful for various applications such as surveillance, access control, or identification systems.
Happy Hacking

