# EXP.NO.3-Simulation-of-Digital-Modulation-Techniques

3. Simulation of Digital Modulation Techniques Such as
   
   i) Amplitude Shift Keying (ASK)
   
   ii) Frequency Shift Keying (FSK)
   
   iii) Phase Shift Keying (PSK)


# AIM:

To simulate digital modulation techniques such as ASK, FSK, and PSK using Python and analyze their waveforms.



# SOFTWARE REQUIRED:

Python (Google Colab or Jupyter Notebook)

Libraries: numpy, matplotlib



# ALGORITHMS:

Amplitude Shift Keying (ASK):
Define binary data.

Set carrier frequency and sampling rate.

Generate time vector.

Generate message and carrier signals.

Modulate using ASK: Multiply carrier with data bits.

Plot message, carrier, and ASK signal.

Frequency Shift Keying (FSK):
Define binary data.

Set two different frequencies for 1 and 0.

Create a time vector and message signal.

Generate modulated signal by selecting frequency according to the bit.

Plot message and FSK signal.

Phase Shift Keying (PSK):
Define binary data.

Set carrier frequency and sampling rate.

Generate message and carrier signal.

Modulate using PSK: Use phase 0 for '1', phase π for '0'.

Plot message, carrier, and PSK signal.





# PROGRAM: ASK


import numpy as np

import matplotlib.pyplot as plt



data = [1, 0, 1, 0, 1, 1, 0, 1]     # Binary data to be transmitted

bit_duration = 1                   # Duration of each bit (in seconds)

fc = 10                            # Carrier frequency (Hz)

amplitude = 2                      # Amplitude of the carrier

sampling_rate = 1000              # Samples per bit


t = np.arange(0, bit_duration * len(data), 1 / sampling_rate)



message_signal = np.repeat(data, sampling_rate)


carrier_signal = amplitude * np.sin(2 * np.pi * fc * t)


ask_signal = np.zeros(len(t))  # Initialize with zeros

for i, bit in enumerate(data):

    if bit == 1:
    
        t_bit = np.arange(0, bit_duration, 1 / sampling_rate)
        
        ask_signal[i * sampling_rate : (i + 1) * sampling_rate] = \
        
            amplitude * np.sin(2 * np.pi * fc * t_bit)
            


plt.figure(figsize=(12, 8))

plt.subplot(3, 1, 1)

plt.plot(t, message_signal, 'b')

plt.title('Message Signal')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude')

plt.grid(True)


plt.subplot(3, 1, 2)

plt.plot(t, carrier_signal, 'r')

plt.title('Carrier Signal')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude')

plt.grid(True)

plt.subplot(3, 1, 3)

plt.plot(t, ask_signal, 'g')

plt.title('ASK Modulated Signal')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude')

plt.grid(True)

plt.tight_layout()

plt.show()

OUTPUT:
![ask python](https://github.com/user-attachments/assets/a9e4650a-651b-44db-8493-b4d12dcb9186)

# FSK CODE:

import numpy as np

import matplotlib.pyplot as plt

data = [1, 0, 1, 0, 1, 1, 0, 1]

bit_duration = 1

fc1 = 15                   # Frequency for binary 1

fc0 = 10                   # Frequency for binary 0

amplitude = 2

sampling_rate = 1000

t = np.arange(0, bit_duration * len(data), 1 / sampling_rate)

message_signal = np.repeat(data, sampling_rate)


reference_carrier = amplitude * np.sin(2 * np.pi * fc1 * t)

fsk_signal = np.zeros(len(t))

for i, bit in enumerate(data):

    t_bit = np.arange(0, bit_duration, 1 / sampling_rate)
    
    if bit == 1:
    
        fsk_signal[i * sampling_rate : (i + 1) * sampling_rate] = \
        
            amplitude * np.sin(2 * np.pi * fc1 * t_bit)
            
    else:
    
        fsk_signal[i * sampling_rate : (i + 1) * sampling_rate] = \
        
            amplitude * np.sin(2 * np.pi * fc0 * t_bit)
            

plt.figure(figsize=(12, 8))

plt.subplot(3, 1, 1)

plt.plot(t, message_signal, 'b')

plt.title('Message Signal')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude')

plt.grid(True)

plt.subplot(3, 1, 2)

plt.plot(t, reference_carrier, 'gray')

plt.title('Reference Carrier Signal (15 Hz)')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude')

plt.grid(True)

plt.subplot(3, 1, 3)

plt.plot(t, fsk_signal, 'g')

plt.title('FSK Modulated Signal')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude')

plt.grid(True)

plt.tight_layout()

plt.show()

# OUTPUT:
![fsk python](https://github.com/user-attachments/assets/ac9efe49-338a-4cda-8c43-478b5e09b4a1)

# PSK CODE:

import numpy as np

import matplotlib.pyplot as plt

data = [1, 0, 1, 0, 1, 1, 0, 1]    # Binary data

bit_duration = 1                   # Duration of each bit

fc = 10                            # Carrier frequency (Hz)

amplitude = 2                      # Amplitude of the carrier

sampling_rate = 1000              # Samples per bit

t = np.arange(0, bit_duration * len(data), 1 / sampling_rate)

message_signal = np.repeat(data, sampling_rate)

carrier_signal = amplitude * np.sin(2 * np.pi * fc * t)

psk_signal = np.zeros(len(t))

for i, bit in enumerate(data):

    t_bit = np.arange(0, bit_duration, 1 / sampling_rate)
    
    if bit == 1:
    
        psk_signal[i * sampling_rate : (i + 1) * sampling_rate] = \
        
            amplitude * np.sin(2 * np.pi * fc * t_bit)
            
    else:
    
        psk_signal[i * sampling_rate : (i + 1) * sampling_rate] = \
        
            amplitude * np.sin(2 * np.pi * fc * t_bit + np.pi)

plt.figure(figsize=(12, 8))

plt.subplot(3, 1, 1)

plt.plot(t, message_signal, 'b')

plt.title('Message Signal')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude')

plt.grid(True)

plt.subplot(3, 1, 2)

plt.plot(t, carrier_signal, 'gray')

plt.title('Carrier Signal (10 Hz)')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude')

plt.grid(True)

plt.subplot(3, 1, 3)

plt.plot(t, psk_signal, 'g')

plt.title('PSK Modulated Signal')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude')

plt.grid(True)

plt.tight_layout()

plt.show()

# OUTPUT:
![psk python](https://github.com/user-attachments/assets/0ce7340a-67a8-48f7-9665-0c6f6a2f4392)


# RESULT / CONCLUSION:
ASK, FSK, and PSK modulation techniques were successfully simulated using Python.







