# HIL-based Augmented ICS (HAI) Security Dataset
The HAI dataset was collected form a realistic industiral control syste (ICS) testbed augmented with Hardware-In-the-Loop (HIL) simulator that emulates steam-turbine power generation and pumped-sotrage hydropower generation. 

## License
This work is licensed under a <a href="http://creativecommons.org/licenses/by-sa/3.0/
"> Creative Commons Attribution-ShareAlike License (CC BY-SA 4.0)</a>.

## Content
- [HAI Testbed](#hai-testbed)
- [Dataset](#dataset)
- [Getting the Dataset](#getting-the-dataset)
- [Evaluation](#evaluation)
- [Projects using the Dataset](#projects-using-the-dataset)
- [Changes](#changes)
- [Authors](#Authors)
- [References](#references)



## HAI Testbed
This dataset was developed for research on anomyaly detection in industrial control system (ICS) such as railways, water treatment and power plants. In 2017, we initially lanuched three lab-scale ICS testbed and then built a complex process system combining them with a Hardware-In-the-Lopp (HIL) simulator that emulates thermal power gneration and pumped-storage hudropy generation in 2018. This system integration makes their variables are highly coupled and correlated, which is for the richer dataset. So we named our testbed "HIL-based Augmented ICS". 
The testbed consists of 4 different processes: boiler, turbine, water-treatement and HIL simulation:
* Boiler process: a water-to-water heat trasfer process with low pressurees and moderate temperature, controlled by Emerson's Ovatio DCS
* Turbine process: a rotor kit testbed that closely simulates actual rotating machine behavior, controlled by GE;s Mark VIe DCS
* Water-treatment process: a water feed process that includes a pump to feed water to the upper reservoir and a level control valve to release back into the lower reservoir, controlled by Siemens S7-300 PLC
* HIL simulation: Both of the obiler and turbine processes are interconnected to reamin sychronous with the rotating speed of the virtual steam-trubine power generation model. The pump and value in the water-treatment process are controlled by the pumped-storage hydropower generation model. The dSPACe(R) SCALEXIO for HIL device is interconnected with the real-world processes via Simens S7-1500 PCL and ET200 remote IO device for data-acquisition system based on OPC gateway.

## Dataset
The dataset was collected 57 points every seconde from a real-world ICS testbed enhanced with a HIL (Hardware-In-the-Loop) simulator. The normal situation's dataset was about 7 days. The attack dataset was collected with 34 attack scenarios on 6 Process Control Loops (PCLs). that are distributed and operated on 3 controllers (GE MarkVIe DCS, Emerson Ovation DCS and Siemens S7-1500). The attack dataset consists of one day's worth od data with 20 attacks scenarios on each control loop and two days's worht of data with 14 attacks on multiple control loops. 

_Note: A PCL is a system made up of all control logics needed for the measurements and adjustment of a variable that controls and individual process_

#### Data Files
The data is preseneted into 4 CSV files seperatly for two normal datasets and two attack datasets. 

#### Data Fields 
Refer to Dataset Technical Manual for the details of the below columns.

| time                  |P1.B2004        | P2.B2016| ...  | P4.HT_LD  | attack   | attack.P1   |    ...          | attack.P4 |
|:---:                  | :---:           |  :---:  |  :---: |  :---:  |  :---:   |   :---:     |  :---:         | :---:   |
|20190926 13:00:00+09:00| 0              | 0       | ...   |  0       |  1     |   0       |    ...      | 0   |
|20190926 13:00:01+09:00| 0             | 0       | ...   |  0       |  1     |   0       |    ...      | 0   |
|20190926 13:00:02+09:00| 0            | 0       | ...   |  0       |  1     |   0       |    ...      | 0   |
|20190926 13:00:03+09:00| 0            | 0       | ...   |  0       |  1     |   0       |    ...      | 0   |
|20190926 13:00:04+09:00| 0            | 0       | ...   |  0       |  1     |   0       |    ...      | 0   |
| ``` #column01 ```        | ``` #column02 ``` | ``` #column3 ```| ...  | ``` #column57 ``` | ``` #column58 ```| ``` #column59 ``` | ... |``` #column62 ```|



## Getting the dataset
The dataset will be released in __Februray 2020.__  

> #git

## Evaluation
It is strongly recommended to use the [TaPR (Time-series Aware Precision and Recall)][3] method for evaluating your anomaly detection algorithm, which gives fairness to performance comparisons with other sutides. Got something to suggest? [Let us know!](mailto:hws23@nsr.re.kr)

## Projects using the dataset
Here are some projects and experiments that are using or featuring the dataset in interesting ways. Got something to add? [Let us know!](mailto:hkshin721@nsr.re.kr)

## Changes
* Now - preparing for initial release

## Authors
This repository created in 2020 by Hyeok-Ki Shin, Woomyo Lee and Jeong-Han Yun.

## References
1. Hyeok-Ki Shin, Woomyo Lee, Jeong-Han Yun, and HyoungChun Kim, "[Implementation of Programmable CPS Testbed for Anomaly Detection][1]", 12th USENIX Workshop on Cyber Security Experimentation and Test (CSET 19), Santa Clara, CA, 2019.
2. Hwang, Won-Seok and Yun, Jeong-Han and Kim, Jonguk and Kim, HyoungChun Kim, "[Time-Series Aware Precision and Recall for Anomaly Detection: Considering Variety of Detection Result and Addressing Ambiguous Labeling][2]", CIKM '19:Proceedings of the 28th ACM International Conference on Information and Knowledge Management, pp.2241-2244, 2019.

[3]: https://github.com/saurf4ng/TaPR "TaPR Github"
[1]: https://www.usenix.org/conference/cset19/presentation/shin "Testbed paper"
[2]: https://dl.acm.org/doi/10.1145/3357384.3358118 "TaPR paper"



## Dataset Metadata
The following table is necessary for this dataset to be indexed by search
engines such as <a href="https://g.co/datasetsearch">Google Dataset Search</a>.
<div itemscope itemtype="http://schema.org/Dataset">
<table>
  <tr>
    <th>property</th>
    <th>value</th>
  </tr>
  <tr>
    <td>name</td>
    <td><code itemprop="name">HIL-based Augmented ICS Security Dataset</code></td>
  </tr>
  <tr>
    <td>alternateName</td>
    <td><code itemprop="alternateName">HAI Security Dataset</code></td>
  </tr>
  <tr>
    <td>alternateName</td>
    <td><code itemprop="alternateName">hai seucrity dataset</code></td>
  </tr>
  <tr>
    <td>url</td>
    <td><code itemprop="url">https://github.com/icsdataset/hai</code></td>
  </tr>
  <tr>
    <td>sameAs</td>
    <td><code itemprop="sameAs">https://github.com/icsdataset/hai</code></td>
  </tr>
  <tr>
    <td>description</td>
    <td><code itemprop="description">The HAI dataset was collected form a realistic industiral control syste (ICS) testbed augmented with Hardware-In-the-Loop (HIL) simulator that emulates steam-turbine power generation and pumped-sotrage hydropower generation. 
 </code></td>
  </tr>
  <tr>
    <td>provider</td>
    <td>
      <div itemscope itemtype="http://schema.org/Organization" itemprop="provider">
        <table>
          <tr>
            <th>property</th>
            <th>value</th>
          </tr>
          <tr>
            <td>name</td>
            <td><code itemprop="name"> ICSDataset </code></td>
          </tr>
          <tr>
            <td>sameAs</td>
            <td><code itemprop="sameAs">https://github.com/icsdataset</code></td>
          </tr>
        </table>
      </div>
    </td>
  </tr>
  <tr>
    <td>license</td>
    <td>
      <div itemscope itemtype="http://schema.org/CreativeWork" itemprop="license">
        <table>
          <tr>
            <th>property</th>
            <th>value</th>
          </tr>
          <tr>
            <td>name</td>
            <td><code itemprop="name">CC BY 4.0</code></td>
          </tr>
          <tr>
            <td>url</td>
            <td><code itemprop="url">https://creativecommons.org/licenses/by/4.0/</code></td>
          </tr>
        </table>
      </div>
    </td>
  </tr>
   <tr>
    <td>citation</td>
    <td><code itemprop="citation">https://www.usenix.org/conference/cset19/presentation/shin</code>
      <code itemprop="citation">https://dl.acm.org/doi/10.1145/3357384.3358118
      </code></td>
  </tr>
</table>
</div>
