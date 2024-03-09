.. _proc_dsp:

Signal Processing / Digital Signal Processing
#############################################

A :abbr:`DSP (Digital Signal Processor)` is a specialized microprocessor designed to efficiently **manipulate digital signals** in real-time. It excels in tasks like filtering, modulation, and compression, crucial in audio, video, and telecommunications. Unlike general-purpose processors, DSPs are optimized for numerical calculations and possess dedicated hardware to accelerate signal processing algorithms.

Some microcontrollers, like certain from the *STM32* family, include that kind of specific calculation core.

For example, Arm® Cortex-M4 cores feature a Floating point unit (FPU) single precision which supports all Arm® single-precision data-processing instructions and data types. They also implement a full set of DSP instructions.

|

To learn more about *signal processing*, I suggest you this ressource : `Mixed Signal and DSP Design Techniques <https://www.analog.com/en/resources/technical-books/mixed_signal_dsp_design_book.html>`_ produced by *Analog Devices*.
And for those who lack time, this page : `Beginner's guide to dsp <https://www.analog.com/en/lp/001/beginners-guide-to-dsp.html>`_ by *Analog Devices*.

Data types
==========

DSP operations use **digital data**, coming from the sampling of a signal in the case of signal processing. It can use either floating-point or fixed-point formats.

Arm® Cortex-M4 cores contain a Floating point unit (FPU) single precision.

CMSIS-DSP library
=================

To access to all the features on Arm® Cortex-M4 cores, Arm&trade; in conjunction with silicon, tools and middleware partners developed a vendor-independent **hardware abstraction layer** for all Cortex® processor based devices, called the Arm® **Cortex® Microcontroller Software Interface Standard** (or **CMSIS**).

The idea behind CMSIS is to provide a consistent and simple `software interface <https://github.com/ARM-software/CMSIS_5>`_ to the
processor for interface peripherals, real-time operating systems, and middleware,
simplifying software re -use, reducing the learning curve for new microcontroller
developments and reducing the time to market for new devices.

This hardware abstraction layer includes the **CMSIS-DSP** library that facilites the access to the DSP features of Arm® Cortex-M4 cores. This library includes especially : 

* Fast mathematical functions, like sine and cosine
* Complex mathematical functions like calculating magnitude
* Filtering functions like FIR or IIR
* Transform functions like FFT
* Controller functions like PID controller

You can download the latest version on the `CMSIS-DSP GitHub repository <https://github.com/ARM-software/CMSIS-DSP>`_.

