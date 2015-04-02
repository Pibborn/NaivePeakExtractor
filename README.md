# NaivePeakExtractor
a naive peak magnitude spectrogram extractor, written in python. it takes a Yaafe magnitude spectrum analysis as input, and shows a magnitude spectrogram and its peaks.

## dependencies
- `scipy`
- `matplotlib`
- `numpy`

## usage
run `NaivePeakExtractor.py analysis-files/[any file]`, or provide your own Yaafe spectral magnitude analysis file.

## q&a
- those .csv files are huge!

yes, they are included so that anyone can run an example extraction without having to install yaafe, which could be inconvenient.

- that's a lot of peaks!

yes, maybe more than expected. one would think that we should take as peaks only the time-frequency points where magnitude is at the highest throughout the track; however, doing so would result in a very sparse representation of the sound, as the loud segments have more peaks than the quiet ones. for fingerprinting purposes, we would like to be able to recognize both quiet and loud audio. so the spectrogram peaks are computed analysis-frame-wise, taking the highest magnitude fft bins in each time frame.

however, this approach does have its limits. if you look at the peaks extracted for the white noise track, you'll see that that's a little too much :) there are many things one can do to limit situations like this. in previous work, my approach has been to divide the frequency spectrum in bands and only take the highest magnitude bin from each band as a peak. this limits the number of peaks we take from each frame but assures us we will have a dense representation of the original sound. however, this one is a naive peak extractor, so this approach has not been implemented :)

- I run the script with no errors, but nothing happens.

have you used matplotlib previously? it could be a problem with the default settings in matplotlib. you may want to look [here](https://stackoverflow.com/questions/7534453/matplotlib-does-not-show-my-drawings-although-i-call-pyplot-show). if you were not going to provide your own analysis file, you could also just look at the `plot-images` folder and trust me that's what you were going to get :)
