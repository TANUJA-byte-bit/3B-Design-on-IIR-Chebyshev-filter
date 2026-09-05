# IIR-FILTER-DESIGN

# EXP 3 B: DESIGN OF LOW PASS CHEBYSHEV IIR FILTER USING BILINEAR TRANSFORMATION

# AIM: 

# To a design of low pass Chebyshev IIR filter using Bilinear Transformation.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc;
close;
wp=input('Enter the pass band frequency (Radians) = ');
ws=input('Enter the stop band frequency (Radians) = ');
alphap=input('Enter the pass band attenuation (dB) = ');
alphas=input('Enter the stop band attenuation (dB) = ');
T=input('Enter the value of sampling time = ');
omegap=(2/T)*tan(wp/2);
disp(omegap,'omegap = ');
omegas=(2/T)*tan(ws/2);
disp(omegas,'omegas = ');
N=acosh(sqrt(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1)))/(acosh(omegas/omegap));
disp(N,'N = ');
N=ceil(N);
disp(N,'Round off value of N = ');
omegac=omegap/(((10^(0.1*alphap))-1)^(1/(2*N)));
disp(omegac,'omegac = ');
Epsilon=sqrt((10^(0.1*alphap))-1);
disp(Epsilon,'Epsilon = ');
[pols,gn]=zpch1(N,Epsilon,omegap);
disp(gn,'Gain');
disp(pols,'Poles');
hs=poly(gn,'s','coeff')/real(poly(pols,'s'));
disp(hs,'Analog Low Pass Chebyshev Filter Transfer Function');
z=poly(0,'z');
Hz=horner(hs,(2/T)*((z-1)/(z+1)));
disp(Hz,'Digital LPF Transfer Function H(Z) = ');
HW=frmag(Hz,512);
w=0:%pi/511:%pi;
plot(w/%pi,abs(HW));
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of Chebyshev IIR LPF');
```

# OUTPUT: 

<img width="707" height="552" alt="image" src="https://github.com/user-attachments/assets/900d7698-b6f0-4d1f-a31c-2a76c9102402" />
<img width="847" height="867" alt="image" src="https://github.com/user-attachments/assets/d4a52a61-a1e4-4ddf-8781-7eef95648a8a" />
<img width="788" height="1403" alt="image" src="https://github.com/user-attachments/assets/632e1a4d-8e74-4e77-868f-ddbe609ab255" />
<img width="780" height="1371" alt="image" src="https://github.com/user-attachments/assets/b9bfc5eb-4398-4381-8dbd-6e34cd1cec4a" />
<img width="1157" height="1600" alt="image" src="https://github.com/user-attachments/assets/475d5361-c232-4e27-8447-55433492090b" />


# RESULT: 

Thus design of Chebyshev Low pass IIR filter waveforms were plotted and output was
verified.
