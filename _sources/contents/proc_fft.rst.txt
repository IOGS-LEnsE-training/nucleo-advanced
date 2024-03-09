Signal Processing / Real-time FFT
#################################

Fast Fourier Transform vs Fourier transform
*******************************************

The **Fast Fourier Transform** (FFT) is an algorithm that computes the **Discrete Fourier Transform** (DFT) of a sampled signal. By breaking down a signal into its constituent frequencies, FFT enables analysis and processing in various fields such as signal processing, communications, and image processing.

:abbr:`FFT (Fast Fourier Transform)` transforms a signal from its time (or spatial - for images) domain into the frequency domain. It accomplishes this by recursively dividing the DFT into smaller DFTs, significantly reducing computation time compared to the standard DFT calculation, making it a fundamental tool for spectral analysis and signal processing applications.

Fourier Transform calculation
=============================

The **Fourier transform** of a function :math:`f(t)` is given by the following formula:

.. math:: 

	\hat{f}(\omega) =  \mathcal{F}\{f(t)\}(\omega) = \int_{-\infty}^{\infty} f(t) \cdot e^{-i\omega t} \, dt

Sampling a signal
=================

To obtain the FFT of a function :math:`f(t)`, this function must be **sampled** at a specific frequency called **sampling frequency**, or :math:`F_S`. We can also use the sampling period :math:`T_S = F_S^{-1}`.

Sampling a function :math:`f(t)` on a regular grid means representing the continuous function by a discrete set of function values :math:`f(t_1)`, :math:`f(t_2)`, :math:`f(t_n)`, ... where :math:`t_1 = 1 \cdot T_S`, :math:`t_2 = 2 \cdot T_S`, :math:`t_n = n \cdot T_S`.

Samples can be defined with the following formula : 

.. math::
	
	x[n] = f(t_n) = f(n \dot T_S)
	
To perfectly 


DFT calculation
===============

Based on this sampling, the :abbr:`DFT (Discrete Fourier Transform)` can be calculated by integrating

.. math::

	X[k] = \sum_{n=0}^{N-1} x[n] \cdot e^{-i\frac{2\pi}{N} kn}, \quad k = 0, 1, \ldots, N-1


Digital Signal Processing in microcontrollers
*********************************************

A :abbr:`DSP (Digital Signal Processor)` is a specialized microprocessor designed to efficiently manipulate digital signals in real-time. It excels in tasks like filtering, modulation, and compression, crucial in audio, video, and telecommunications. Unlike general-purpose processors, DSPs are optimized for numerical calculations and possess dedicated hardware to accelerate signal processing algorithms.

Some microcontrollers, like certain from the *STM32* family, include that kind of specific calculation core.

Data types
==========

DSP operations use **digital data**, coming from the sampling of a signal in the case of signal processing. It can use either floating-point or fixed-point formats

CMSIS library
=============

https://www.st.com/resource/en/application_note/dm00273990-digital-signal-processing-for-stm32-microcontrollers-using-cmsis-stmicroelectronics.pdf

https://web.cs.ucdavis.edu/~okreylos/PhDStudies/Winter2000/SamplingTheory.html#:~:text=Sampling%20a%20function%20f(x,cw%2C%20see%20Figure%205.

http://lense.institutoptique.fr/nucleo-obtenir-le-spectre-dun-signal-en-temps-reel-4/

The Arm Cortex® Microcontroller Software Interface Standard (CMSIS) is a
vendor-independent hardware abstraction layer for all Cortex® processor based devices.
CMSIS has been developed by Arm® in conjunction with silicon, tools and middleware
partners.
The idea behind CMSIS is to provide a consistent and simple software interface to the
processor for interface peripherals, real-time operating systems, and middleware,
simplifying software re -use, reducing the learning curve for new microcontroller
developments and reducing the time to market for new devices.
CMSIS library comes with ST firmware under \Drivers\CMSIS\.
The CMSIS-DSP library includes:
• Basic mathematical functions with vector operations
• Fast mathematical functions, like sine and cosine
• Complex mathematical functions like calculating magnitude
• Filtering functions like FIR or IIR
• Matrix computing functions
• Transform functions like FFT
• Controller functions like PID controller
• Statistical functions like calculating minimum or maximum
• Support functions like converting from one format to another
• Interpolation functions



FFT with Nucleo
***************

Creating an MBED6 project
=========================




CMSIS-DSP library
=================

Adding a library by right-click on the active project and select 

.. figure:: ../_static/images/process/fft/keil_add_mbed_library.png
	:width: 70%

In the popup window, paste the GitHub link : https://github.com/ARM-software/CMSIS-DSP then click Next

.. figure:: ../_static/images/process/fft/keil_add_mbed_library_link.png
	:width: 50%

Select the version of the library then click Finish.

.. figure:: ../_static/images/process/fft/keil_add_mbed_library_version.png
	:width: 50%

The library is adding in the project.

.. figure:: ../_static/images/process/fft/keil_add_mbed_library_dl.png


Adding a .mbedignore file
=========================

Adding a new file by right-click on the active project and select *New File*.

Create a :file:`.mbedignore` file.

.. figure:: ../_static/images/process/fft/keil_add_mbed_library_mbedignore.png
	:width: 40%

.. code::

	cmsis-dsp/Examples/*
	cmsis-dsp/PythonWrapper/*
	cmsis-dsp/Scripts/*
	cmsis-dsp/Testing/*
	cmsis-dsp/ComputeLibrary/*

	cmsis-dsp/Source/BasicMathFunctions/BasicMathFunctions.c
	cmsis-dsp/Source/BasicMathFunctions/BasicMathFunctionsF16.c
	cmsis-dsp/Source/BayesFunctions/BayesFunctions.c
	cmsis-dsp/Source/BayesFunctions/BayesFunctionsF16.c
	cmsis-dsp/Source/CommonTables/CommonTables.c
	cmsis-dsp/Source/CommonTables/CommonTablesF16.c
	cmsis-dsp/Source/ComplexMathFunctions/ComplexMathFunctions.c
	cmsis-dsp/Source/ComplexMathFunctions/ComplexMathFunctionsF16.c
	cmsis-dsp/Source/ControllerFunctions/ControllerFunctions.c
	cmsis-dsp/Source/DistanceFunctions/DistanceFunctions.c
	cmsis-dsp/Source/DistanceFunctions/DistanceFunctionsF16.c
	cmsis-dsp/Source/FastMathFunctions/FastMathFunctions.c
	cmsis-dsp/Source/FastMathFunctions/FastMathFunctionsF16.c
	cmsis-dsp/Source/FilteringFunctions/FilteringFunctions.c
	cmsis-dsp/Source/FilteringFunctions/FilteringFunctionsF16.c
	cmsis-dsp/Source/InterpolationFunctions/InterpolationFunctions.c
	cmsis-dsp/Source/InterpolationFunctions/InterpolationFunctionsF16.c
	cmsis-dsp/Source/MatrixFunctions/MatrixFunctions.c
	cmsis-dsp/Source/MatrixFunctions/MatrixFunctionsF16.c
	cmsis-dsp/Source/QuaternionMathFunctions/QuaternionMathFunctions.c
	cmsis-dsp/Source/StatisticsFunctions/StatisticsFunctions.c
	cmsis-dsp/Source/StatisticsFunctions/StatisticsFunctionsF16.c
	cmsis-dsp/Source/SVMFunctions/SVMFunctions.c
	cmsis-dsp/Source/SVMFunctions/SVMFunctionsF16.c
	cmsis-dsp/Source/TransformFunctions/TransformFunctions.c
	cmsis-dsp/Source/TransformFunctions/TransformFunctionsF16.c
	cmsis-dsp/Source/WindowFunctions/WindowFunctions.c

.. caution::

	Be careful to let a blank line at the end of this file.


Main program
============



Sampling application
--------------------

.. code-block:: cpp
	:linenos:

	#include "mbed.h"

	DigitalOut myled(D3);
	AnalogIn   myADC(A1);
	AnalogOut  myDAC(D13);
	Ticker     timer;

	void sample(){
		myled = !myled;
		float val_in = myADC.read();
		myDAC.write(val_in);
	}

	int main() {
		timer.attach(&sample, 40us);	//40us 25KHz sampling rate

		while(1) {
			thread_sleep_for(10);
		}
	}



Final code
----------

.. code-block:: cpp
	:linenos:

	#include "mbed.h"
	#include "arm_math.h"
	#include "arm_common_tables.h"
	#include "arm_const_structs.h"

	#define SAMPLES                 512             
	/* 256 real party and 256 imaginary parts */
	#define FFT_SIZE                SAMPLES / 2     
	/* FFT size is always the same size as we have samples, so 256 in our case */
	#define OUTPUT_GAIN             10.0
	/* Gain on the output values - for better display */

	float32_t Input[SAMPLES];
	float32_t Output[FFT_SIZE];

	bool      trig=0;         // sampling blocking semaphore
	int       indice = 0;

	DigitalOut myled(D3);
	AnalogIn   myADC(A1);
	AnalogOut  myDAC(D13);
	Ticker     timer;

	void sample(){
		myled = 1;
		if(indice < SAMPLES){
			Input[indice] = myADC.read() - 0.5f;    
			// Real part NB removing DC offset
			Input[indice + 1] = 0;                  
			// Imaginary Part set to zero
			indice += 2;
		}
		else{ trig = 0; }
		myled = 0;
	}

	int main() {
		float maxValue;            // Max FFT value is stored here
		uint32_t maxIndex;         // Index in Output array where max value is

		while(1) {
			if(trig == 0){
				timer.detach();
				// arm_cfft_sR_f32_lenXXX, where XXX is the samples number, here 256
				arm_cfft_f32(&arm_cfft_sR_f32_len256, Input, 0, 1);
	 
				// FFT calculation and storage of the magnitude of the complex FFT values in the Output array
				arm_cmplx_mag_f32(Input, Output, FFT_SIZE);
				Output[0] = 0;
			
				// Analog display of the FFT
				myDAC=1.0f;     // Sync pulse
				wait_us(10);    
				myDAC=0.0f; 
				// Display all the values
				for(int i=0; i < FFT_SIZE; i++){
					myDAC.write(OUTPUT_GAIN * Output[i]/FFT_SIZE); 
				}
				myDAC=0.0f;
				
				// Restart sampling
				trig = 1;
				indice = 0;
				timer.attach(&sample,40us);    //40us 25KHz sampling rate
			}
		}
	}
