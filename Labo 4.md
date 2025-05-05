IIR = infinite impulse response

## windowed sinc filter
[scientist.com](https://www.analog.com/media/en/technical-documentation/dsp-book/dsp_book_Ch16.pdf)

## oef1
```scilab
clc;
clf;

fs = 2000;
samplesize = 1/fs;
x = 0:samplesize:0.05;

f = 100;
sqr = 2 * squarewave(2 * %pi * f * x) + 2;
plot(x, sqr);
a = gca(); // Get current axes
a.data_bounds(3) = -1;
a.data_bounds(4) = 5; // Set upper Y limit to 5

f5th = 5 * f;
frq = [(f5th-10) / fs, (f5th + 10) / fs];
hz = iir(6, "sb", "cheb1", frq, [0.1, 0]);

filtered_sqr = flts(sqr, hz);
plot(x, filtered_sqr, "r");

```

## oef2
```scilab
clc;
clf;

fs = 1000;
Ts = 1/fs
x = 0:Ts:1;

input_sig = sin(2 * %pi * 70 * x) + sin(2 * %pi * 50 * x) + sin(2 * %pi * 130 * x);

fstop1 = 70;
fpass1 = 120;

fc = fstop1 + ((fpass1 - fstop1) / 2);

// filter kernel points
dF = (fpass1 - fstop1) / fs;
disp(dF);
M = ceil(4 / dF);

if modulo(M, 2) == 0 then
    M = M + 1;
end

disp(M)

// kernel
// sinc 
n = -(M-1)/2 : (M-1)/2;
sinc_kernel = sin(2 * %pi * fc * n / fs) ./ (%pi * n);
sinc_kernel(n == 0) = 2 * fc /fs;

m = 0:M-1
blackman = 0.42 - 0.5 * cos((2 * %pi * m) / M-1) + 0.08 * cos((2 * %pi * m) / M-1)
lowpass_kern = sinc_kernel .* blackman;
delta = zeros(1, M);
delta((M+1)/2) = 1; // center impulse
kern = delta - lowpass_kern;

subplot(4,1,1)
plot(m, blackman);
xtitle("blackman window");
subplot(4, 1, 2)
plot(n, kern);
xtitle("Filter Kernel");

// response
freq_resp = fft(kern);
N = length(kern);
f = (0:N/2) * (fs / N)
subplot(4,1,3)
plot(f, abs(freq_resp(1:(N/2)+1)));
xtitle("frequency response")

filtered_sig = conv(input_sig, kern, "same");
subplot(4,1,4)
plot(x, input_sig, "r");
plot(x, filtered_sig, "b");
legend(["input signal", "filtered signal"])

```

## oef3
```scilab
clc;
clf;

fs = 1000;
Ts = 1/fs
x = 0:Ts:1;

input_sig = sin(2 * %pi * 25 * x) + sin(2 * %pi * 70 * x) + sin(2 * %pi * 50 * x) + sin(2 * %pi * 130 * x);

fstop1 = 30;
fpass1 = 40;
fpass2 = 70;
fstop2 = 120;

fc_low = fstop1 + ((fpass1 - fstop1) / 2);
fc_high = fpass2 + ((fstop2 - fpass2) / 2);

// filter kernel points
dF = (fc_high - fc_low) / fs;
disp(dF);
M = ceil(4 / dF);

if modulo(M, 2) == 0 then
    M = M + 1;
end

disp(M);


// kernel
// sinc 
n = -(M-1)/2 : (M-1)/2;
sinc_kernel_low = sin(2 * %pi * fc_low * n / fs) ./ (%pi * n);
sinc_kernel_high = sin(2 * %pi * fc_high * n / fs) ./ (%pi * n);
sinc_kernel_low(n == 0) = 2 * fc_low /fs;
sinc_kernel_high(n==0) = 2 * fc_high / fs;
sinc_kernel = sinc_kernel_high - sinc_kernel_low;

m = 0:M-1;
blackman = 0.42 - 0.5 * cos((2 * %pi * m) / M-1) + 0.08 * cos((2 * %pi * m) / M-1);
kern = sinc_kernel .* blackman;

subplot(4,1,1)
plot(m, blackman);
xtitle("blackman window");
subplot(4, 1, 2)
plot(m, kern);
plot(m, sinc_kernel_high, "r");
plot(m, sinc_kernel_low, "g");
xtitle("Filter Kernel");
legend(["kernel", "sinc kernel high", "sinc kernel low"]);

// response
freq_resp = fft(kern);
N = length(kern);
f = (0:N/2) * (fs / N);
subplot(4,1,3);
plot(f, abs(freq_resp(1:(N/2)+1)));
xtitle("frequency response")

filtered_sig = conv(input_sig, kern, "same");
subplot(4,1,4)
plot(x, input_sig, "r");
plot(x, filtered_sig, "b");
legend(["input", "filtered signal"])

```
