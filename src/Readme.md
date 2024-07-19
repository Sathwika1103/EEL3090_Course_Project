# Project
## Implementation of SVM algorithm on STM32 discovery board
### Team : Sriharsha Gandyadapu (B21CS029), Sathwika Gavva (B21CS030)

* ### <b>Introduction</b>
The project aims to implement the Support Vector Machine (SVM) algorithm on an STM32 Discovery board for classification tasks using the MNIST dataset. The STM32F429I DISC1 is a powerful development board based on the ARM Cortex-M4 processor, providing a range of peripherals and features suitable for embedded applications. 

* ### <b>Instructions to run</b>
    #### Model Training
    1) We will use a svm model trained using tensorflow (Refer from svm_model.ipynb).
    2) Now using the model that has been trained, we need to convert it to the TensorFlow Lite Model that our microcontroller can use. TensorFlow has a built-in converter function that will save the model as a TensorFlow Lite model file. (Download svm_mnist.tflite)
    3) To get our tflite file to run on a microcontroller, we need to save it as a constant byte array in svm_model.h file.

    ### Project Configuration
    1) In STM32CubeIDE, Install X-CUBE-AI latest version.
    2) Create a new project: Click File > New > STM32 Project. And In the Target Selection window, click on the Board Selector tab and select the board (“STM2F429I-DISC1” for me).
    3) In CubeMX, enable Timer 16, and set the prescaler and AutoReload register with the maximum value and also select the Artificial Intelligence component class in Additional Software sub-tab.
    4) Select STMicroelectronics.X-CUBE_AI and ensure that it is activated in Mode pane. In the Configuration pane, add network and Select TFLite for the network type and browse the svm_mnist.tflite downloaded earlier.
    5) Click the Analyze button, we can get an overview of the model. This can be helpful for figuring out memory required to store it and how many multiply-and-accumulate (MAC) operations are needed.
    6) Validate on Desktop runs some tests with models to make sure that inference works. 
    7) Head to the Clock Configuration tab. Under PLL Source Mux, change the input to the high speed internal clock, labeled HSI. For HCLK (MHz), enter the value “80” and the CubeMX software should adjust all of the prescalers to give you an 80 MHz system clock.
    8) And then generate the code.We can now see a new X-CUBE-AI library appear in the project. In the App folder, we can find a set of source code files with <model_name>.
    9) Open main.c. Take a look at the main.c code. After that Add printf Float Support.
    10) Save the code. Click Project > Build Project. And Run in Debug Mode. Then Click the Play button to start running code on the microcontroller. 
