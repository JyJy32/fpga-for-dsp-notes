# opgave 1
```
clc;
clf; // Clear the figure
scf(0);
rows = 6;

// Define parameters
f = 100;
T = 1/f;
x = 0:1/8000:3*T;
N = length(x);

// A - Signal
y = 3 * sin(2*%pi*f*x);
subplot(rows,1,1);
plot(x, y);
title("Original Signal");

// B - Noise
noise_amp = 0.2;
noise = 2*noise_amp * rand(1, N, "normal") - noise_amp;
subplot(rows,1,2);
plot(x, noise);
title("Noise");

// C - Noisy Signal
noise_input = y + noise;
subplot(rows,1,3);
plot(x, noise_input);
title("Noisy Signal");

// D - Moving Average Filter

function out=maf(signal, Nf)
    out = zeros(1, length(signal))
    sm = 0;
    for i = 1:length(signal)
        if i > Nf
            sm = sm - signal(i -Nf)
        end
        sm = sm + signal(i);
        out(i) = sm / Nf
    end
    out
endfunction

// Overlay filtered signal
subplot(rows,1,4);
fil_10 = maf(noise_input, 10);
fil_5 = maf(noise_input, 5)
plot(x, fil_10, 'r');
plot(x, fil_5, "g");
legend(["factor 10", "factor 5"])
title("filters")

// apply filter to inout signal

filtered5 = conv(noise_input, fil_5, "same");
subplot(rows, 2, 9);
plot(x, filtered5);
filtered = conv(noise_input, fil_10, "same");
subplot(rows, 2, 10);
plot(x, filtered);

// step response
// this isnt needed there's a squarewave function in scilab, it's a fun learning experience tho
// block_wave = zeros(1, length(x));
// for k = 1:1000
//    block_wave = block_wave + (1/(2*k - 1) * sin(2 * %pi* f *(2*k - 1) * x));
// end

block_wave = squarewave(2 * %pi * f * x);
subplot(rows, 1, 6);
plot(x, block_wave);
square_fil_5 = maf(block_wave, 5);
plot(x, square_fil_5, "g");
square_fil_10 = maf(block_wave, 10);
plot(x, square_fil_10, "r");
legend(["Square", "factor 5", "factor 10"]);
set(gca(),'data_bounds',[min(x),min(block_wave)-0.1; max(x),max(block_wave) + 0.1]);

figure();
// bode factor 5
fil_5 = ones(1, 5) / 5;
fil_poly = poly(fil_5, "z", "coeff");
fil_horner = horner(fil_poly, (1/%z));
fil_sys_5 = syslin("d", fil_horner);
subplot(1, 2, 1);
bode(fil_sys_5);

fil_10 = ones(1, 10) * 1/10;
fil_poly = poly(fil_10, "z", "coeff");
fil_horner = horner(fil_poly, (1/%z));
fil_sys_10 = syslin("d", fil_horner);
subplot(1, 2, 2);
bode(fil_sys_10);
```

