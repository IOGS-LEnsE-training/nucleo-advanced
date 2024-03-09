.. _proc_samp:

Signal Processing / Sampling
############################

**Sampling** in digital signal processing involves measuring the value of a continuous-time signal at specific intervals, known as **samples**. These samples are then used to represent the original signal in a discrete form. 

Sampling is essential for various applications, including audio processing, image processing, and digital communication systems. It allows for the efficient representation and manipulation of continuous signals in the digital domain, enabling a wide range of digital processing and analysis techniques.

Analog vs Digital Signal
************************

An **analog signal** consists of a continuous signal changing over time.

A **digital signal** is a list of numbers, called **samples**, encoded in a specific format.

For example, an analog electric signal can be converted into a series of digital samples by using an analog-to-digital converter (ADC). The inverse encoding is also possible by using a digital-to-analog converter (DAC).

Sampling a Signal
*****************

Main Objective
==============

One of the main objectives of converting an analog signal into a digital format, which computers (or equivalent systems, like microcontrollers) can store, is to be able to **restore this signal later**.

To achieve this, it is necessary to **know the sampling instants** perfectly. Two methods are possible:

* non-uniform sampling or irregular sampling,
* uniform sampling.

Non-uniform Sampling
--------------------

In non-uniform sampling, the sampling instants are **not evenly spaced**. Instead, they can be irregularly distributed across time. This approach can be useful in certain scenarios where a constant sampling frequency is not practical or when specific sampling instants are required for specific purposes, such as compressive sensing or certain types of data acquisition systems.

In this context, it's necessary to store the samples **and** the instants of sampling.

However, non-uniform sampling typically introduces additional challenges in signal processing and reconstruction compared to uniform sampling. Specialized techniques are often needed to properly process and reconstruct signals sampled in this manner.

This method is **not commonly used** for digital signal processing.

Uniform Sampling
----------------

In uniform sampling, the sampling instants are evenly spaced at a constant rate throughout time. This is the **most common method of sampling signals** and is widely used in various digital signal processing applications. Uniform sampling simplifies many aspects of signal processing, including reconstruction and filtering, because the spacing between samples is consistent.

The constant rate is called **sampling frequency**, or :math:`F_S`. We can also use the sampling period :math:`T_S = F_S^{-1}`.

In the rest of this document, we will assume **regular sampling** at a constant sampling frequency.

Sampled Signal
==============

Sampling a function :math:`f(t)` on a regular grid means representing the continuous function by a discrete set of function values :math:`f(t_1)`, :math:`f(t_2)`, :math:`f(t_n)`, ... where :math:`t_1 = 1 \cdot T_S`, :math:`t_2 = 2 \cdot T_S`, :math:`t_n = n \cdot T_S`.

Samples can be defined with the following formula:

.. math::
	
	x[n] = f(t_n) = f(n \cdot T_S)


Sampling Limit
**************

The **Nyquist–Shannon sampling theorem** states that in order to accurately reconstruct a continuous signal from its samples, the **sampling frequency** must be at least **twice** the **highest frequency** present in the signal. This criterion ensures that no information is lost during the sampling process, allowing for faithful reconstruction of the original signal. 

The theorem is fundamental in digital signal processing and underpins the design and implementation of analog-to-digital conversion systems, digital audio, and various digital communication technologies.

