# EXP 1 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
```
clc;
clear;

// Input sequences
x = [1,2,3,0];
h = [4,5,6,0];

L = length(x);
M = length(h);
N = L + M - 1;
y = zeros(1, N);

// Convolution
for n = 0:N-1
    for k = 0:L-1
        if (n-k >= 0 & n-k < M) then
            y(n+1) = y(n+1) + x(k+1) * h(n-k+1);
        end
    end
end

// Display result
disp("Linear Convolution:");
disp(y);

// Plot (stem style)
n = 0:N-1;
clf();
plot2d3(n, y);     // Stem plot
xtitle("Linear Convolution Output", "n", "y[n]");

```

## PROGRAM (Circular Convolution): 
```
clc;
clear;

// Input sequences
x = [1 2 2 1];
h = [1 2 3 1];

// Length for circular convolution (take max length)
N = max(length(x), length(h));

// Zero padding if needed
x = [x, zeros(1, N-length(x))];
h = [h, zeros(1, N-length(h))];

disp("Zero-padded input:");
disp(x);
disp("Zero-padded impulse:");
disp(h);

// ---- Circular convolution using modulo ----
y = zeros(1, N);

for n = 1:N
    for k = 1:N
        j = pmodulo(n-k, N) + 1;   // pmodulo avoids negative indices
        y(n) = y(n) + x(k) * h(j);
    end
end

disp("Circular convolution result:");
disp(y);

// ---- Plot results ----
subplot(3,1,1);
plot2d3(0:N-1, x);
title("Input sequence x[n]");
xlabel("n"); ylabel("Amplitude");

subplot(3,1,2);
plot2d3(0:N-1, h);
title("Impulse response h[n]");
xlabel("n"); ylabel("Amplitude");

subplot(3,1,3);
plot2d3(0:N-1, y);
title("Circular Convolution y[n]");
xlabel("n"); ylabel("Amplitude");
```

// Circular Convolution

## OUTPUT (Linear Convolution): 
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9cc55050-c6bf-45ea-9d5e-7f48dea9caa8" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/c189a5af-d91c-4b2d-a913-195cdc4886b0" />


## OUTPUT (Circular Convolution): 
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/570ecf03-5a17-4009-a905-d07a51617106" />

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/9b7ea73c-004d-4f7d-96bf-aabdfa36d0c4" />

## RESULT: 
Thus,the Linear and Circular Convolution is verified
