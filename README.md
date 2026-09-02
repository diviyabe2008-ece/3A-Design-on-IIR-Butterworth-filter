# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION AND IMPULSE INVARIENT TECHNIQUE

# AIM: 

 To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PART-1
# BILINEAR TRANSFORMATION

# PROGRAM: 
```
clc ;
close ;
wp=input('Enter the pass band frequency (Radians )= ' );
ws=input('Enter the stop band frequency (Radians )= ' );
alphap=input( ' Enter the pass band attenuation (dB)=' );
alphas=input( ' Enter the stop band attenuation(dB)=' );
T=input('Enter the Value of sampling Time=');
//Pre warping- Bilinear Transformation
omegap=(2/T)*tan(wp/2);
disp(omegap,'omegap=');
omegas=(2/T)*tan(ws/2);
disp(omegas,'omegas=');
//Order of the filter
N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap));
disp(N,'N=');
N=ceil(N);
disp(N,'Round off value of N=');
//Cut off frequency
omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N)));
disp(omegac,'omegac=');
disp('Normalised Analog LPF Transfer function H(S)=');
hs_Normalised = analpf(N,'butt',[0,0],1);
disp(hs_Normalised);
disp('Analog LPF Transfer function H(S)=');
hs= analpf(N,'butt',[0,0],omegac);
disp(hs);
z=poly(0,'z');//Defining variable z
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation
disp('Digital LPF Transfer function H(Z)=');
disp(Hz);
HW=frmag(Hz,512); // Frequency response
w=0:%pi/511:%pi ;
plot(w/%pi,abs(HW));
xlabel(' Normalized Digital Frequency w');
ylabel('Magnitude ');
title(' Frequency Response of Butterworth IIR LPF');
```


# OUTPUT: 

<img width="753" height="692" alt="image" src="https://github.com/user-attachments/assets/cb457f41-65e8-44f3-a724-e94b3fd989ed" />



<img width="636" height="937" alt="image" src="https://github.com/user-attachments/assets/7d5babe1-aa7d-4548-9de8-02ebf3e0d6cd" />



# MANUAL CALCULATION:
<img width="896" height="1599" alt="image" src="https://github.com/user-attachments/assets/ec4021a4-d509-4708-8756-14eaf586796c" />



<img width="896" height="1598" alt="image" src="https://github.com/user-attachments/assets/4fae582d-3d7e-491f-9348-ea0488e89d85" />



<img width="1600" height="1514" alt="image" src="https://github.com/user-attachments/assets/24e25a46-f99f-40ee-8bb6-f4f0cf7a7477" />

# PART-2
# IMPULSE INVARIENT METHOD

# PROGRAM 
```
clc; 
clear; 
close; 
// Input specifications 
wp = input('Enter the pass band frequency (Radians)= '); 
ws = input('Enter the stop band frequency (Radians)= '); 
alphap = input('Enter the pass band attenuation (dB)= '); 
alphas = input('Enter the stop band attenuation (dB)= '); 
T = input('Enter the sampling time = '); 
// Convert digital frequencies to analog frequencies
omegap = wp/T; 
disp(omegap,'omegap='); 
omegas = ws/T; 
disp(omegas,'omegas=');
 // Calculate filter order 
N = log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap)); 
disp(N,'N='); 
N = ceil(N); 
disp(N,'Rounded value of N='); 
// Cutoff frequency 
omegac = omegap/((10^(0.1*alphap)-1)^(1/(2*N))); 
disp(omegac,'omegac=');
 // Normalized Analog LPF 
disp('Normalized Analog LPF Transfer Function H(s)'); 
Hs_normal = analpf(N,'butt',[0,0],1); 
disp(Hs_normal); 
// Analog Butterworth LPF
 disp('Analog LPF Transfer Function H(s)'); 
Hs = analpf(N,'butt',[0,0],omegac); 
disp(Hs); 
// Impulse Invariant Transformation 
Hz = dscr(Hs,T); 
disp('Digital LPF Transfer Function H(z)'); 
disp(Hz);
 // Frequency response 
HW = frmag(Hz,512);
 w = 0:%pi/511:%pi; 
plot(w/%pi,abs(HW)); 
xlabel('Normalized Digital Frequency'); 
ylabel('Magnitude');
 title('Frequency Response of Butterworth IIR LPF using Impulse Invariant Method');
```
# OUTPUT
<img width="757" height="687" alt="image" src="https://github.com/user-attachments/assets/c57b2d67-d135-4f8e-8986-f1c250600cfa" />



<img width="680" height="948" alt="image" src="https://github.com/user-attachments/assets/33a08465-2c31-487c-84ef-7fa4264e70c5" />



# MANUAL CALCULATION :
<img width="962" height="1600" alt="image" src="https://github.com/user-attachments/assets/6303c2bd-6816-42ea-8314-e3f345748de2" />



<img width="914" height="1598" alt="image" src="https://github.com/user-attachments/assets/c01fea74-02a8-45ff-8e1c-2614d14989ba" />




# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.

