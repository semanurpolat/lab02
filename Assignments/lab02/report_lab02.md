# Lab Report — Lab 02: MRI Noise Removal via Fourier Notch Filtering

## Overview

The goal of this lab was to remove periodic noise from a corrupted MRI scan using a notch filter in the Fourier domain.

## Implementation

First I looked at the spectrum by computing the log magnitude of the k-space data, then I reconstructed the image from it. The two noise spikes were at (row, col) positions (148, 147) and (108, 109), placed symmetrically around the centre. I built a notch mask with discs of radius 2 around both spikes, multiplied it with the k-space data and reconstructed the filtered image from the masked spectrum.

## Results

The corrupted image had strong diagonal stripes all over it. In the filtered image these stripes are gone and the brain looks like a normal MRI scan again, so the filter removed the noise without damaging the image itself.