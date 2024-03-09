.. _proc_samp:

Signal Processing / Sampling
############################


Sampling in digital signal processing involves measuring the value of a continuous-time signal at specific intervals, known as samples. These samples are then used to represent the original signal in a discrete form. The process of sampling is crucial for converting analog signals, such as sound or images, into digital form for processing by computers and electronic devices.


The sampling theorem states that to accurately reproduce a signal, it must be sampled at a rate greater than twice the maximum frequency present in the signal. This ensures that the original signal can be reconstructed from its samples without loss of information.


Sampling is essential for various applications, including audio processing, image processing, and digital communication systems. It allows for the efficient representation and manipulation of continuous signals in the digital domain, enabling a wide range of digital processing and analysis techniques   .


To obtain the FFT of a function :math:`f(t)`, this function must be **sampled** at a specific frequency called **sampling frequency**, or :math:`F_S`. We can also use the sampling period :math:`T_S = F_S^{-1}`.

Sampling a function :math:`f(t)` on a regular grid means representing the continuous function by a discrete set of function values :math:`f(t_1)`, :math:`f(t_2)`, :math:`f(t_n)`, ... where :math:`t_1 = 1 \cdot T_S`, :math:`t_2 = 2 \cdot T_S`, :math:`t_n = n \cdot T_S`.

Samples can be defined with the following formula : 

.. math::
	
	x[n] = f(t_n) = f(n \dot T_S)



To perfectly 

