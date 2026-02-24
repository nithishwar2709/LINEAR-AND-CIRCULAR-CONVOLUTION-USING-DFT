# EXPT 1: LINEAR-AND-CIRCULAR-CONVOLUTION-USING-DFT
## AIM
To perform and verify linear and circular convolution operation of two given sequences
using SCILAB.
## APPARATUS REQUIRED
PC installed with SCILAB
## PROGRAM:
### LINEAR CONVOLUTION
<br>

```
clc;
clear;

x = [1 1 1 1];
h = [1 2 3 4];

m = length(x);
n = length(h);

a = 0:m-1;
b = 0:n-1;

subplot(3,1,1);
plot2d3(a, x);
xlabel('Time');
ylabel('Amplitude');
title('Graphical Representation of Input Signal x');

subplot(3,1,2);
plot2d3(b, h);
xlabel('Time');
ylabel('Amplitude');
title('Graphical Representation of Impulse Signal h');

y = zeros(1, m+n-1);

for i = 1:m+n-1
    conv_sum = 0;
    for j = 1:m
        if ((i-j+1) >= 1) & ((i-j+1) <= n) then
            conv_sum = conv_sum + x(j) * h(i-j+1);
        end
    end
    y(i) = conv_sum;
end

disp(y, 'Convolution Sum using Direct Formula Method =');

subplot(3,1,3);
plot2d3(0:m+n-2, y);
xlabel('Time');
ylabel('Amplitude');
title('Graphical Representation of Output Signal y');

```
<br>

### CALCULATIONS:
<br>

![20260224_203921](https://github.com/user-attachments/assets/f143a76e-ba90-4e11-a790-84ed439cce0a)
![20260224_203929](https://github.com/user-attachments/assets/cad6f8fc-ec2c-404b-a00d-40674c062d17)

<br>
<br>

### SAMPLE OUTPUT:
<br>
<br>

<img width="1919" height="1199" alt="Screenshot 2026-02-09 091620" src="https://github.com/user-attachments/assets/bd11c55f-c05a-4a1f-a374-299fbd53485d" />

<br>
<br>

## CIRCULAR CONVOLUTION:
<br>
<br>

```
clc;
clear;

x = [1 1 1 1];
n1 = 0:length(x)-1;

subplot(3,1,1);
plot2d3(n1, x);
xlabel('time');
ylabel('amplitude');
title('input sequence');

h = [1 2 3];
n2 = 0:length(h)-1;

subplot(3,1,2);
plot2d3(n2, h);
xlabel('time');
ylabel('amplitude');
title('impulse sequence');

N1 = length(x);
N2 = length(h);
N = max(N1, N2);
N3 = N1 - N2;

if N3 > 0 then
    h = [h zeros(1, N3)];
else
    x = [x zeros(1, abs(N3))];
end

y = zeros(1, N);

for n = 1:N
    for i = 1:N
        j = n - i + 1;
        if j <= 0 then
            j = N + j;
        end
        y(n) = y(n) + x(i) * h(j);
    end
end

disp(y);

n3 = 0:N-1;
subplot(3,1,3);
plot2d3(n3, y);
xlabel('time');
ylabel('amplitude');
title('circular convolution');

```

### CALCULATIONS:

<br>
<br>

![20260224_203935](https://github.com/user-attachments/assets/956299fb-2133-468c-a40a-e0d9818a8e4c)

<br>

### SAMPLE OUTPUT:
<br>

<img width="1919" height="1199" alt="Screenshot 2026-02-23 093554" src="https://github.com/user-attachments/assets/dbfb5f86-0b8a-4a01-bdb9-2f1459b1d8f5" />
<br>
<br>



## RESULT:
Thus, the linear convolution and circular convolution of the two given sequences were performed and its result was verified.
