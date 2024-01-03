## Veo E-scooter Service in Birmingham, AL

In this study, we build a transportation simulation model for Birmingham, AL that supports Veo e-scooter rides. This study directly uses the field data from Veo’s 2021 micromobility pilot deployment in Birmingham, including the detailed ride information of all shared e-scooters from July 2021 to June 2022. The data is shared by Veo as a commitment of their pilot program to the City of Birmingham, where user identities are properly anonymized. 

We explored our dataset and found that rebalancing does occur. Below we show six consecutive rides conducted by the same e-scooter, and we can see that the 3rd ride starts at a location that is a designated parking corral of Veo, moved from where the 2nd ride ends. The e-scooter should have been moved for rebalancing/charging between these two rides.
<p align="center">
  <img src="imgs/re_balance_example.PNG" />
</p>

We group all the rides by e-scooter vehicles, and for each e-scooter, we order its rides by time, and every pair of consecutive rides with the first ending at location *ℓ<sub>a</sub>* and time *t<sub>a</sub>* and the next starting at location *ℓ<sub>b</sub>* and time *t<sub>b</sub>* contributes a data point ⟨dist(*ℓ<sub>a</sub>*, *ℓ<sub>b</sub>*), (*t<sub>b</sub>* − *t<sub>a</sub>*)⟩, where dist(*ℓ<sub>a</sub>*, *ℓ<sub>b</sub>*) denotes the distance between *ℓ<sub>a</sub>* and *ℓ<sub>b</sub>*. The figure below shows a histogram of all the data points partitioned into bins of size 10 meters, and the median of (*t<sub>b</sub>* − *t<sub>a</sub>*) of all the data points in each bin is shown as an orange dot. We can see that most data points have dist(*ℓ<sub>a</sub>*, *ℓ<sub>b</sub>*) close to 0, and dist(*ℓ<sub>a</sub>*, *ℓ<sub>b</sub>*) may be slightly larger than 0 for some data points due to GPS localization precision error. However, there are bins that correspond to longer distances so the e-scooter vehicles are most likely moved, which can also be evidenced from the median time that generally increases with the bin distance. Note that rebalancing takes time so (*t<sub>b</sub>* − *t<sub>a</sub>*) tends to be longer for such bins. We consider all data point ⟨dist(*ℓ<sub>a</sub>*, *ℓ<sub>b</sub>*), (*t<sub>b</sub>* − *t<sub>a</sub>*)⟩ with dist(*ℓ<sub>a</sub>*, *ℓ<sub>b</sub>*) > 200 meters to be a rebalancing move from *ℓ<sub>a</sub>* to *ℓ<sub>b</sub>*, which should have a high confidence.

<p align="center">
  <img src="imgs/re_balance_figure.PNG"/>
</p>

## Spatial-Temporal Network KDE
E-scooter pickup-locations (in green), and the Spatial-Temporal Network KDE to understand the data distribution.

<p align="center">
  <img src="imgs/veo_pickups_stnkde.gif" />
</p>


## Visualizing MATSim Results using <a href="https://simunto.com/via/">Via</a>

Click on the image below to open the YouTube video.

<div align="center">
  <a href="https://youtu.be/44mI1Xs8o3A"><img src="imgs\via_img.svg" alt="IMAGE ALT TEXT"></a>
  <p align="center">Urban traffic simulation with e-scooter services around 7:00 AM</p>
</div>
<br>