# DSBSC


EX NO: 2	DSB-SC-AM MODULATOR AND DEMODULATOR

AIM:

To write a program to perform DSBSC modulation and demodulation using SCI LAB and study its spectral characteristics

EQUIPMENTS REQUIRED

•	Computer with i3 Processor
•	SCI LAB

Note: Keep all the switch faults in off position

Algorithm:

1.	Define Parameters:
•	Fs: Sampling frequency.
•	T: Duration of the signal.
•	Fc: Carrier frequency.
•	Fm: Frequency of the message signal.
•	Amplitude: Maximum amplitude of the message signal.
2.	Generate Signals:
•	Message Signal: A sinusoidal signal that will be modulated.
•	Carrier Signal: A high-frequency sinusoidal signal used for modulation.
3.	DSBSC Modulation:
•	Modulated Signal: Multiply the message signal by the carrier signal to produce the DSBSC signal.
4.	DSBSC Demodulation:
•	Multiplication: Multiply the modulated signal by the carrier signal to get the product of the message signal with itself (i.e., the original message signal plus high-frequency components).
•	Low-pass Filtering: Apply a Butterworth low-pass filter to remove the high- frequency components and recover the original message signal.
5.	Visualization:
Plot the message signal, carrier signal, DSBSC modulated signal, and the recovered signal after demodulation.
PROCEDURE

•	Refer Algorithms and write code for the experiment.
•	Open SCILAB in System
•	Type your code in New Editor
•	Save the file
 
•	Execute the code
•	If any Error, correct it in code and execute again
•	Verify the generated waveform using Tabulation and Model Waveform

Model Waveform

<img width="703" height="679" alt="image" src="https://github.com/user-attachments/assets/e7c7c7f8-ccf2-41ac-b1f3-325989941a6f" />

Program
clc;
clear;
close;

Am = 8.2;
Ac = 16.4;
fm = 390;
fc = 3900;
fs = 39000;
t = 0:1/fs:0.01;

// Message and Carrier
modulating = Am * sin(2 * %pi * fm * t);
carrier = Ac * sin(2 * %pi * fc * t);

// DSB-SC Modulation (product modulation)
dsb_sc = modulating .* carrier;

// Coherent Demodulation
demod_raw = dsb_sc .* carrier;

// Low-pass filter using moving average
N = round(fs / (5 * fm));
lp = ones(1, N) / N;
demodulated = conv(demod_raw, lp, 'same');
demodulated = demodulated - mean(demodulated);

// Plot all signals
subplot(4,1,1)
plot(t, modulating)
title('Modulating Signal')
xlabel('Time (s)')
ylabel('Amplitude')

subplot(4,1,2)
plot(t, carrier)
title('Carrier Signal')
xlabel('Time (s)')
ylabel('Amplitude')

subplot(4,1,3)
plot(t, dsb_sc)
title('DSB-SC Modulated Signal')
xlabel('Time (s)')
ylabel('Amplitude')

subplot(4,1,4)
plot(t, demodulated)
title('Demodulated Signal (Recovered Message)')
xlabel('Time (s)')
ylabel('Amplitude')

Output Graph
<img width="610" height="460" alt="image" src="https://github.com/user-attachments/assets/6f47cf60-b899-4beb-8c11-11600c48e1f6" />


Tablular Column
<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/dacf771d-372c-433f-81d2-056203806857" />
<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/8c1790ac-20de-493f-97d5-a4d3e9b8fdc7" />



Result

Thus the DSB-SC-AM Modulation and Demodulation is generated.

