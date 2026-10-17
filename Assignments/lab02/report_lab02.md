# Lab Report — Lab 02: MRI Noise Removal via Fourier Notch Filtering

## Overview

The goal of this lab was to remove periodic noise from a corrupted MRI scan with a notch filter in the Fourier domain. The noise shows up as diagonal stripes in the image and as two sharp spikes in the k-space data.

## Implementation

I first computed the log magnitude of the k-space data and reconstructed the corrupted image. The two noise spikes were at (row, col) = (148, 147) and (108, 109). They sit symmetrically around the centre (128, 128), which is what you expect for a real-valued sinusoid. Then I made a notch mask with a disc of radius 2 around each spike, multiplied it with the k-space data and reconstructed the filtered image from the masked spectrum.

## Results

The corrupted image had strong diagonal stripes everywhere. After filtering the stripes are gone and the brain structure is clearly visible again. The spikes are around 2.4 × 10⁶ while the median of the spectrum is only about 845, so they are by far the brightest points. The mask removes only 26 of 65,536 frequencies, so almost nothing else in the image is affected. Radius 2 is a bit larger than strictly needed because the spikes are very sharp, but it is a safe choice when reading the positions from the plot.