Visual Representation of the Frame Processing Loop
=======================================
while True:  # ← Infinite loop for continuous processing
    │
    ├─ ret, frame = cap.read()          # 📷 Capture ONE frame from camera
    │                                   #    frame = numpy array (480x640x3)
    │
    ├─ results = model(frame)           # 🧠 YOLO processes THIS SINGLE FRAME
    │                                   #    Returns: detected objects in THIS frame only
    │
    ├─ create_label_box(results, frame) # ✏️ Draw boxes & labels on THIS FRAME
    │     │                             #    Modifies the frame array directly
    │     ├─ cv2.rectangle()            #    Draws green rectangles
    │     └─ cv2.putText()              #    Adds text labels
    │
    ├─ cv2.imshow(frame)                # 📺 Display THIS PROCESSED FRAME
    │
    └─ Next iteration → NEW FRAME       # 🔄 Loop back for next frame