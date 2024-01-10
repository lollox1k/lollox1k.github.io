- The alpha rhythm is an oscillatory component of the spontaneous EEG. The frequency of oscillation of the alpha rhythm is around 10 Hz. The amplitude of the EEG in the alpha band decreases when the generating region of the cerebral cortex becomes engaged in a functional task (visual, motor). The proper (visual) alpha rhythm is generated in the occipital lobe of the cerebral cortex. The amplitude of the alpha rhythm is not constant, but rather “waxes and wanes” with irregular periods, with changes occurring often after an interval in the order of 1 second. The alpha band of the EEG is conventionally limited between 8 and 13 Hz. The alpha rhythm can be observed by filtering the spontaneous EEG signal using a narrowband filter, with cutoff frequencies at 8 and 13 Hz (approximately).
- The mu rhythm is an oscillatory component of the spontaneous EEG, whose frequency is in the alpha band. The mu rhythm is generated in the central regions of the cerebral cortex. The oscillations of mu rhythm are more “arc-shaped”, rather than resembling a regular sinewave.

- The delta and theta frequency bands identify frequencies lower than those in the alpha band
- The beta and gamma frequency bands identify frequencies higher than those in the alpha band.

- Evoked Potentials are deflection of the EEG signal following the presentation of a sensory input.
- Event related potentials include evoke potentials, as well as EEG responses to motor or cognitive events.

- EEG electrodes made of silver with a layer of silver chloride (Ag/AgCl) are non-polarizable, thus allow recording of extremely slow-changing potentials
- In the EEG terminology, impedance is a measure of the quality of the contact between electrode and scalp, through the conductive gel
- Contact impedance of the electrodes is measured in kiloOhm (�Ω) and must be measured using an alternating current.
- Gold electrodes are polarizable, thus they should not be used to measure slowly changing potentials.
- The Common-Mode Rejection Ratio (CMRR) of a bipolar amplifier characterizes the ratio between the gain of the difference of potential between input electrodes and the
  gain of the common potential with respect to ground.
- The CMRR is usually expressed in decibel (dB) and high values characterizes better amplifiers.
- The advantage of a high CMRR amplifier is that it suppresses common-mode disturbances such as powerline (50 Hz) noise.
- The measurement of a single EEG signal requires three electrodes – two as input to the differential amplifier and one to provide the ground potential.
- The input impedance of a biosignal amplifier must be many orders of magnitude higher than the contact impedance of the electrodes. It is usual to have input impedances
in the order of 108 Ω.
- EEG guidelines suggest keeping the electrodes’ contact impedance below 5 �Ω. The use of modern amplifiers with high input impedance allow to relax this requirement.
One of the reasons why one should keep the electrodes’ contact impedance much lower than the amplifier’s input impedance is that the resulting a voltage divider would
otherwise reduce the measured potential.
The difference of contact impedances of electrodes should be small compared to the input difference of the differential amplifier, otherwise the resulting unbalance
compromises its common-mode rejection capability.
The electrode labels of the International 10-20 System uses the first letter of the four lobes of the cerebral cortex (Frontal, Parietal, Occipital, Temporal), plus “C” (central) to
designate electrodes over the central sulcus.
In the electrode labels of the International 10-20 System, odd/even number designate electrodes on the left/right side, respectively
The International 10-20 System for EEG electrodes placement takes its name because the distance between adjacent electrodes is 10% or 20% of the distance between pairs
of reference points on the skull (Nasion and Inion, or preauricular points)
In monopolar EEG recordings, a single reference potential is used for all recorded channels. The reference electrode is placed on scalp position that are assumed to be far
from the electrical sources of interest, such as the earlobes.
The position of the reference electrode can strongly influence the shape and amplitude of EEG potentials. The profile (i.e. disregarding the actual potential value) of scalp
topographies are not influenced.
In bipolar EEG recordings, each channel is the difference of potential between two adjacent electrodes. It is mostly used in clinical settings to highlight features of interest at
visual inspection of the waveforms.
EEG signals recorded in monopolar configuration can be re-referenced to the Common Average Reference (CAR), by subtracting from each channel the instantaneous
average of all channels. In ideal conditions, this would approximate taking the reference potential at infinity.

An EEG artifact is a potential difference due to sources outside the brain.
Artifacts can have biological origin (such as eyes, muscles heart), can be due to external electromagnetic generators (power supply, engines, etc) or to events affecting
the recording setup (electrode movements or loss of contact, saturation of the ADC).
Artifacts can be partially attenuated or removed through signal processing during data analysis, but it is always preferable to make all efforts to prevent them when the
signal is being acquired
The eye is more positive in its frontal part (cornea) than its posterior part (retina), and thus its movements can generate large artifacts (EOG) on the EEG (of the order
of 500��)
During an eyeblink, the eyelid shortcuts the positive potential of the external surface of the eye, causing positive deflections of the EEG with amplitude of several
hundreds of microvolt and duration of a few hundreds of milliseconds.
A sudden upwards/downwards movement of the eyes generates a positive/negative deflection of EEG potentials (EOG) on frontal EEG channels, respectively.
A sudden movement of the eyes to the right/left generates a positive/negative deflection of EEG potentials (EOG) on the EEG channel F8, respectively.
The electrical activity of the muscles (EMG) has a spectral content starting at frequencies of 20 Hz and up, thus affecting the beta and gamma bands of the EEG signal
The amplitude of the electromyogram (EMG) originated from muscles in the head can have amplitude ten times higher than the EEG signal (thus in the order of 1 ��).
EMG artifact can easily appear on the EEG recording unless the subjects are specifically instructed by the experimenter on how to relax their face and tongue/throat
muscles.
The heart activity can contaminate an EEG recording because an electrocardiographic (ECG/EKG) artifact can directly affect the potentials, especially if the reference
electrode is not placed on the head.
The heart activity can contaminate an EEG recording because a ballistocardiographic artifact is indirectly generated by the pulse of a blood vessel causing movements
of a nearby electrode.
Sweating can affect the EEG, causing a slow changing and high amplitude artifact (below 0.5 Hz, up to a few mV)
Powerline noise is an artifact caused by the capacitive coupling between (i) the conductors carrying the alternating (typically at 50Hz) current power supply and (ii) the
recording setup including the subject.
The powerline noise affects a very narrow frequency band of the recorded signal around 50 Hz (or 60 Hz, depending on the powerline frequency). Other frequency
bands can be affected at multiple frequencies that at multiple (typically odd multiples) of 50/60Hz.
Powerline noise is accentuated by asymmetries in the recording electrode pairs, such as impedances and cable path, because asymmetries prevent the noise to be
rejected by the amplifier’s common-mode rejection capabilities.
Notch filters effectively remove powerline noise because they selectively reject the narrow band affected by the artifact, preserving almost entirely the useful signal.
Movement of the subject’s head may produce slow artifacts on the EEG recording, whose waveform is closely related to the timecourse of the movement. Since the

potentials originate from the mechanical displacement of the charged double layer at the electrodes interface, these artifacts are less pronounced when non-
polarizable electrodes

As a preliminary step to EEG data analysis, the following data can be discarded: (i) one or more channels, if it is extensively contaminated by artifacts; (ii) all time intervals (epochs) in which artifacts appear. Both strategies
can be applied on the same dataset.
The estimation of event-related or evoked potentials (ERPs, EPs) requires the acquisition of numerous repetitions (typically tens or hundreds) of the stimulus or event which evoked or induced the potential.
When recording ERPs or EPs (whose peak amplitudes are a few microvolts down to a fraction of microvolt), the spontaneous EEG (whose amplitude is of tens of microvolt) is to be considered a noise that completely masks
the EPs or ERPs on the recorded waveform.
In ERP analysis, the averaging procedure consists in (i) segmenting epochs (trials) with fixed duration from the raw recording, each aligned to a repetition of the event; (ii) performing a synchronized average, i.e. averaging all
corresponding samples sharing the same latency across the set of trials.
Synchronized averaging of � trials preserves the amplitude of the ERP and reduces the amplitude of the background spontaneous EEG activity by a factor √�, under commonly verified hypotheses.
The amplitude of ERPs is measured with respect to a baseline epoch (usually preceding the stimulus), in which the amplitude is assumed to be zero.
The latency of a ERP peak is measured with respect to the relevant event, usually the presentation of a stimulus, rather than with respect to the beginning of the waveform.
In an ERP, peaks are named with a leading P (N) if the peak has positive (negative) polarity.
In an ERP, peaks are often named with a trailing number indicating the nominal latency in milliseconds. In older conventions, the trailing number represents the order of the peak within the ERP.
A negative peak in a ERP recorded on a specific subject with a latency of 108 ms may still be named N100, if it matches the physiological phenomenon of the nominal N100 component.
The Stimulus Onset Asynchrony (SOA) measures the time interval between the onset two successive stimuli in a train. If each trial only contains a stimulus, it is equivalent to the Inter-Trial Interval (ITI)
The Inter-Stimulus Interval (ISI) measures the time interval between the end of a stimulus and the beginning of the following one. It equals the SOA minus the stimulus duration.
In an ERP, the response to a stimulus has a reduced amplitude when the SOA is too short. Long-latency components of the ERP are especially sensitive to this decrease.
... tradeoff between number of stimuli and SOA ...
... mapping...
Brain activity in response to a stimulus can be phase-locked to the event, meaning that the whole timecourse (including positive and negative peaks) of the response has the same latency in every repetition. This activity is
called evoked
Brain activity in response to a stimulus can be non-phase-locked, meaning that they show variable latency (jitter) at each repetition. This activity is called invokedinduced.
The averaging procedure can reliably uncover components of an ERP corresponding to evoked activity of the brain.
Induced activity is often examined by analyzing the envelope of the EEG in a relevant frequency band, i.e. by rectifying or squaring the pass-band filtered trials before averaging them.
In the EEG terminology, synchronization (desynchronization) is synonymous of an increase (decrease) of the waveform amplitude (and thus power).
Event-Related Desynchronization/Synchronization (ERD/S) quantify changes of the power of EEG relative to a baseline period, expressed as percent change. ERD/S is usually evaluated on a whole range of relevant latencies
with respect to the event.
Computation of ERD/S from a set of N EEG trials requires the following steps: (i) band-pass filtering in the relevant frequency band; (ii) take the square of each sample; (iii) take a synchronized average across trials; (iv)
smooth by averaging samples within each short time window in a set of adjacent ones covering the whole timecourse; (iv) compute the relative percentage change with respect to the average value in a baseline period.
Clarification: An alternative algorithm to evaluate the ERD/S uses rectification instead of squaring in step (ii), thus estimating the amplitude of the signal rather than its power.
Time-frequency analysis allows to analyze and visualize changes of the spectral components of a signal over time. Time resolution and frequency resolution cannot be freely chosen – the higher the one, the lower the other.