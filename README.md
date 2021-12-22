
# HIL-based Augmented ICS (HAI) Security Dataset
The HAI dataset was collected from a realistic industiral control system (ICS) testbed augmented with a Hardware-In-the-Loop (HIL) simulator that emulates steam-turbine power generation and pumped-storage hydropower generation. 

Click [here](https://github.com/icsdataset/hai/blob/master/hai_dataset_technical_details_v2.0.pdf) to find out more about HAI dataset.
> Please e-mail us [here](mailto:hkshin721@nsr.re.kr?subject=[GitHub-HAI]%20) if you have any questions about the dataset.

## Contents
- [Background](#background)
- [HAI Testbed](#hai-testbed)
- [HAI Dataset](#hai-dataset)
- [Getting the Dataset](#getting-the-dataset)
- [Performance Evaluation](#performance-evaluation)
- [Projects using the Dataset](#projects-using-the-dataset)
- [Change Log](#change-log)
- [Authors](#Authors)
- [References](#references)


## Background

- In 2017, three laboratory-scale CPS testbeds were initially launched, namely GE’s turbine testbed, Emerson’s boiler testbed, and FESTO’s modular production system (MPS) water-treatment testbed. These testbeds were related to relatively simple processes, and were operated independently of each other.

- In 2018, a complex process system was built to combine the three systems using a hardware-in-the-loop (HIL) simulator, where thermal power generation and pumped-storage hydropower generation were simulated. This ensured that the variables were highly coupled and correlated for a richer dataset. In addition, an open platform communications united architecture (OPC-UA) gateway was installed to facilitate data collection from heterogeneous devices.

- The first version of HAI dataset, HAI 1.0,  was made available on GitHub and Kaggle in February 2020. This dataset included ICS operational data from both normal and anomalous situations for 38 attacks. Subsequently, a debugged version of HAI 1.0, namely HAI 20.07, was released for the HAICon 2020 competition in August 2020.

-  HAI 21.03 was released in 2021, and is based on a more tightly coupled HIL simulator to produce clearer attack effects with additional attacks. This provided more quantitative information and covers a variety of operational situations and better insights into the dynamic changes of the physical system.

## HAI Testbed
The testbed consists of four different processes: boiler, turbine, water-treatement and HIL simulation:

- **Boiler Process (P1):** A water-to-water heat-trasfer process with low pressure and moderate temperature. It is controlled by Emerson's Ovation DCS.
- **Turbine Process (P2):** A rotor kit process that closely simulates the behavior of an actual rotating machine. It is controlled by GE's Mark VIe DCS.
- **Water-treatment Process (P3):** A water-treatment process that includes the pumping of water to the upper reservoir and releasing it back into the lower reservoir. It is controlled by Siemens's S7-300 PLC.

- **HIL Simulation(P4):** Both of the boiler and turbine processes are interconnected to reamin sychronous with the rotating speed of the virtual steam-trubine power generation model. The pump and value in the water-treatment process are controlled by the pumped-storage hydropower generation model. The dSPACE's SCALEXIO system is used for HIL simulations and is interconnected with the real-world processes through a Siemens S7-1500 PLC and ET200 remote IO devices for data-acquisition system based on OPC gateway.


## HAI Dataset
Two major versions of HAI datasets have been released thus far. Each dataset consists of several CSV files, and each file satisfies time continuity. The quantitative summary of each version are as follows:
> **Note:** The **version numbering** follows a **date-based scheme**, where the version number indicates the released date of HAI dataset.  HAI 20.07 is the bug-fixed one of the first version HAI v1.0 released in February 2020.
<table align=center>
    <thead  align=center>
        <tr bgcolor='#aaaaaa'>
            <th rowspan=2>Version</th>
            <th rowspan=2>Data Points</th>
            <th colspan=3>Normal Dataset</th>
            <th colspan=4>Attack Dataset</th>
        </tr>
         <tr>
            <th>Files</th>
            <th>Interval</th>
            <th>Size</th>
            <th>Files</th>
            <th>Attack Count</th>
            <th>Interval</th>
            <th>size</th>
        </tr>
    </thead>
    <tbody>
        <tr bgcolor='#dddddd'>
            <td rowspan=5 align=center><b><a href="https://github.com/icsdataset/hai/tree/master/hai-21.03"> HAI 21.03<a></b> </td>
            <td rowspan=5> 78 points/sec</td>
            <td>train1.csv</td>
             <td align=right>60 hours</td>
             <td align=right>100 MB</td>
             <td> test1.csv</td>
             <td align=right>5 attacks</td>
             <td align=right>12 hours</td>
             <td align=right>22 MB</td>
        </tr>
        <tr >
             <td>train2.csv</td>
             <td align=right>63 hours</td>
             <td align=right>116 MB</td>
             <td>test2.csv</td>
             <td align=right>20 attacks</td>
             <td align=right>33 hours</td>
             <td align=right>62 MB</td>
        </tr>
        <tr bgcolor='#dddddd'>
            <td>train3.csv</td>
             <td align=right>229 hours</td>
             <td align=right>246 MB</td>
             <td>test3.csv</td>
             <td align=right>8 attacks</td>
             <td align=right>30 hours</td>
             <td align=right>56 MB</td>
        </tr>
        <tr>
            <td rowspan=2 colspan=3> </td>
             <td>test4.csv</td>
             <td align=right>5 attacks</td>
             <td align=right>11 hours</td>
             <td align=right>20 MB</td>
        </tr>
          <tr bgcolor='#dddddd'>
             <td>test5.csv</td>
             <td align=right>12 attacks</td>
             <td align=right>26 hours</td>
             <td align=right>48 MB</td>
        </tr>
        <tr >
            <td rowspan=2 align=center> <b><a href="https://github.com/icsdataset/hai/tree/master/hai-20.07"> HAI 20.07<a> </b><br> (HAI1.0)</td>
            <td rowspan=2> 59 points/sec</td>
            <td>train1.csv</td>
             <td align=right>86 hours</td>
             <td align=right>127 MB</td>
             <td>test1.csv</td>
             <td align=right>28 attacks</td>
             <td align=right>81 hours</td>
             <td align=right>119 MB</td>
        </tr>
           <tr bgcolor='#dddddd'>
            <td>train1.csv</td>
             <td align=right>91 hours</td>
             <td align=right>98 MB</td>
             <td>test1.csv</td>
             <td align=right>10 attacks</td>
             <td align=right>42 hours</td>
             <td align=right>62 MB</td>
        </tr>
    </tbody>
</table>




### Data fields 
The time-series data in each CSV file satisfies time continuity. The first column represents the observed time as “yyyy-MM-dd hh:mm:ss,” while the rest columns provide the recorded SCADA data points. The last four columns provide data labels for whether an attack occurred or not, where the attack column was applicable to all process and the other three columns were for the corresponding control processes.
> Refer to the **latest technical manual** for the details for each column.

| time                  |P1_B2004        | P2_B2016| ...  | P4_HT_LD  | attack   | attack_P1   |    ...          | attack_P3 |
|:---:                  | :---:           |  :---:  |  :---: |  :---:  |  :---:   |   :---:     |  :---:         | :---:   |
|20190926 13:00:00| 0.09830         |1.07370       | ...   |  0       |  0    |   0       |    ...      | 0   |
|20190926 13:00:01| 0.09830        | 1.07410      | ...   |  0       |  1     |   0       |    ...      | 1  |
|20190926 13:00:02| 0.09830        | 1.07380        | ...   |  0       |  1     |   0       |    ...      | 1   |
|20190926 13:00:03| 0.09830        | 1.07360       | ...   |  0       |  1     |   1       |    ...      | 1   |
|20190926 13:00:04| 0.09830         | 1.07430        | ...   |  0       |  1     |  1      |    ...      | 1 |




## Getting the dataset
>  **NOTICE:** All data files are compressed by the standard GNU zip (gzip) due to a strict maximum size limit of 100 MB for individual files in a repository.

Type ```git clone```, and the paste the below URL. 
```
$ git clone https://github.com/icsdataset/hai
```
To unzip multiple gzip files, you can use:
```
$ gunzip *.gz
```
## Performance Evaluation
It is strongly recommended to use the [TaPR (Time-series Aware Precision and Recall)](https://github.com/saurf4ng/TaPR) method for evaluating your anomaly detection algorithm, which gives fairness to performance comparisons with other sutides. Got something to suggest? [Let us know!](mailto:hws23@nsr.re.kr?subject=[GitHub-TaPR]%20)

## Projects using the dataset
Here are some projects and experiments that are using or featuring the dataset in interesting ways. Got something to add? [Let us know!](mailto:dolgam@nsr.re.kr?subject=[GitHub-HAI]%20)
        
### HAICon (Online AI Competition for ICS Threat Detection)
 * HAICon 2020 : https://dacon.io/competitions/official/235624/overview/description
 * HAICon 2021 : https://dacon.io/en/competitions/official/235757/overview/description
        
## Change Log
Please refer to the technical manual for the detailed changes 
 * HAI 21.03 release (2021-03-25)
 * HAI 20.07 release (2020-07-22) 
* Initial release (2020-02-07) 

## Authors
Created by Hyeok-Ki Shin, Woomyo Lee, Jeong-Han Yun and HyoungChun Kim in the Affiliated Institute of ETRI, Daejeon, South Korea.

## License
This work is licensed under a [Creative Commons Attribution-ShareAlike License (CC BY-SA 4.0)](http://creativecommons.org/licenses/by-sa/4.0/).

## References
1. Hyeok-Ki Shin, Woomyo Lee, Jeong-Han Yun, and HyoungChun Kim, "[HAI 1.0: HIL-based Augmented ICS Security Dataset][1]", 13th USENIX Workshop on Cyber Security Experimentation and Test (CSET 20), Santa Clara, CA, 2020.
2. Hwang, Won-Seok and Yun, Jeong-Han and Kim, Jonguk and Kim, HyoungChun Kim, "[Time-Series Aware Precision and Recall for Anomaly Detection: Considering Variety of Detection Result and Addressing Ambiguous Labeling][2]", CIKM '19:Proceedings of the 28th ACM International Conference on Information and Knowledge Management, pp.2241-2244, 2019.
3. Seungoh Choi, Jeong-Han Yun, Sin-Kyu Kim, "[A Comparison of ICS Datasets for Security Research Based on Attack Paths][3]", In: Luiijf E., Žutautaitė I., Hämmerli B. (eds) Critical Information Infrastructures Security. CRITIS 2018. Lecture Notes in Computer Science, vol 11260. Springer, Cham.

[1]: https://www.usenix.org/conference/cset20/presentation/shin "Dataset paper"
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
