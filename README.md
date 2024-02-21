# zockerBoy

## Path Taken
1. Started off with Color Palette detection:
    1. Used color thief
2. Then went onto make text overlay detection:
    1. Tried using pyTesseract natively
        1. Had issues with implementing it due to bad OCR results
    2. Used cv2 to turn it into bw (better results than rgb)
    3. Used CV2 to make boxes around text and compile it
    4. Used pyTesseract to detect text from those boxes
        1. Had to mess around with the config to see which method gives most matches based on e-media
        2. Added thresholding to it make sure only the high % matches get through
        3. Had to mess around with the threshold to see what works the best
3. Object Detection:
    1. Tried using yoloX
        1. dependancies weren't resolving, wheels weren't building
            1. Severe python interpreter problems faced, had to re-do path
        2. tried moondream
            1. models specified had too varying tensor values, couldn't find a suitable sigmoid loss model for it to fit into
        3. tried mmdetection
            1. it's also viable for commercial usage
            2. had to build gcc/mingw
            3. had to build mmDetection and it's sub-packages from base to work with cuda 12.1 and my version of cuDNN
                1. Built core labelling and idenitfication
                2. Built tracking
                3. Test tracking on image and videos with boxes made
                    1. Used an instance of yoloX for the same (which is also commercially viable)