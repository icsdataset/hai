# HIL-based Augmented ICS (HAI) Security Dataset
The HAI dataset was collected form a realistic industiral control system (ICS) testbed augmented with a Hardware-In-the-Loop (HIL) simulator that emulates steam-turbine power generation and pumped-storage hydropower generation. 

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
This dataset was developed for research on anomaly detection in industrial control systems (ICSs) such as railways, water-treatment, and power plants. In 2017, we initially lanuched three laboratory scale ICS testbeds. In 2018, we built a complex process system that combined the three systems with a Hardware-In-the-Lopp (HIL) simulator that emulates thermal power gneration and pumped-storage hydropower generation, thus ensuring that their variables are highly coupled and correlated for the richer dataset. So we named our testbed "HIL-based Augmented ICS". 
The testbed consists of four different processes: boiler, turbine, water-treatement and HIL simulation:

#### P1: Boiler Process
A water-to-water heat-trasfer process with low pressure and moderate temperature. It is controlled by Emerson's Ovation DCS.

#### P2: Turbine Process
A rotor kit process that closely simulates the behavior of an actual rotating machine. It is controlled by GE's Mark VIe DCS.

#### P3: Water-treatment Process
A water-treatment process that includes the pumping of water to the upper reservoir and releasing it back into the lower reservoir. It is controlled by Siemens's S7-300 PLC.

#### P4: HIL Simulation
Both of the boiler and turbine processes are interconnected to reamin sychronous with the rotating speed of the virtual steam-trubine power generation model. The pump and value in the water-treatment process are controlled by the pumped-storage hydropower generation model. The dSPACE's SCALEXIO system is used for HIL simulations and is interconnected with the real-world processes through a Siemens S7-1500 PLC and ET200 remote IO devices for data-acquisition system based on OPC gateway.


## Dataset
The dataset was built by collecting 59 data points every second from a real-world ICS testbed enhanced with a HIL simulator. The dataset for the normal situation was collected for almost 7 days. The attack dataset was collected with 34 attack scenarios on the six Process Control Loops (PCLs). The PCLs are distributed and operated on 3 controllers (GE MarkVIe DCS, Emerson Ovation DCS and Siemens S7-1500). The attack dataset consists of one day's worth od data with 20 attacks scenarios on each control loop and two days's worht of data with 14 attacks on multiple control loops. 

_Note: A PCL is a system made up of all control logics needed for the measurements and adjustment of a variable that controls and individual process._

#### Data Fields 
Refer to Dataset Technical Manual for the details of the below columns.

| time                  |P1.B2004        | P2.B2016| ...  | P4.HT_LD  | attack   | attack.P1   |    ...          | attack.P3 |
|:---:                  | :---:           |  :---:  |  :---: |  :---:  |  :---:   |   :---:     |  :---:         | :---:   |
|20190926 13:00:00+09:00| 0.09830         |1.07370       | ...   |  0       |  0    |   0       |    ...      | 0   |
|20190926 13:00:01+09:00| 0.09830        | 1.07410      | ...   |  0       |  1     |   0       |    ...      | 1  |
|20190926 13:00:02+09:00| 0.09830        | 1.07380        | ...   |  0       |  1     |   0       |    ...      | 1   |
|20190926 13:00:03+09:00| 0.09830        | 1.07360       | ...   |  0       |  1     |   1       |    ...      | 1   |
|20190926 13:00:04+09:00| 0.09830         | 1.07430        | ...   |  0       |  1     |  1      |    ...      | 1 |
| ``` #column01 ```        | ``` #column02 ``` | ``` #column3 ```| ...  | ``` #column59 ``` | ``` #column60 ```| ``` #column61 ``` | ... |``` #column63 ```|


#### Data Files
The data is preseneted into 4 CSV files seperatly for two normal datasets and two attack datasets. 

_Please note that all data files are compressed by the standard GNU zip (gzip) due to a strict maximum size limit of 100 MB for individual files in a repository._

## Getting the dataset
Type ```git clone```, and the paste the below URL. 
```
$ git clone https://github.com/icsdataset/hai
```
To unzip multiple gzip files, you can use:
```
$ gunzip *.gz
```
## Evaluation
It is strongly recommended to use the [TaPR (Time-series Aware Precision and Recall)](https://github.com/saurf4ng/TaPR) method for evaluating your anomaly detection algorithm, which gives fairness to performance comparisons with other sutides. Got something to suggest? [Let us know!](mailto:hws23@nsr.re.kr)

## Projects using the dataset
Here are some projects and experiments that are using or featuring the dataset in interesting ways. Got something to add? [Let us know!](mailto:hkshin721@nsr.re.kr, wmlee@nsr.re.kr)

## Changes
* Initial release (2020-02-07) 

## Authors
Created by Hyeok-Ki Shin, Woomyo Lee, Jeong-Han Yun and HyoungChun Kim in the Affiliated Institute of ETRI, Daejeon, South Korea.

## References
1. Hyeok-Ki Shin, Woomyo Lee, Jeong-Han Yun, and HyoungChun Kim, "[Implementation of Programmable CPS Testbed for Anomaly Detection][1]", 12th USENIX Workshop on Cyber Security Experimentation and Test (CSET 19), Santa Clara, CA, 2019.
2. Hwang, Won-Seok and Yun, Jeong-Han and Kim, Jonguk and Kim, HyoungChun Kim, "[Time-Series Aware Precision and Recall for Anomaly Detection: Considering Variety of Detection Result and Addressing Ambiguous Labeling][2]", CIKM '19:Proceedings of the 28th ACM International Conference on Information and Knowledge Management, pp.2241-2244, 2019.
3. Seungoh Choi, Jeong-Han Yun, Sin-Kyu Kim, "[A Comparison of ICS Datasets for Security Research Based on Attack Paths][3]", In: Luiijf E., Žutautaitė I., Hämmerli B. (eds) Critical Information Infrastructures Security. CRITIS 2018. Lecture Notes in Computer Science, vol 11260. Springer, Cham.

[1]: https://www.usenix.org/conference/cset19/presentation/shin "Testbed paper"
[2]: https://dl.acm.org/doi/10.1145/3357384.3358118 "TaPR paper"
[3]: https://link.springer.com/chapter/10.1007/978-3-030-05849-4_12 "ICS Datasets"


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
    <td><code itemprop="description">The HAI security dataset was collected from a realistic Industiral Control System (ICS) testbed augmented with a Hardware-In-the-Loop (HIL) simulator that emulates steam-turbine power generation and pumped-storage hydropower generation. 
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
            <td><code itemprop="name">The Affiliated Institute of ETRI, South Korea</code></td>
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
