

# HAI (HIL-based Augmented ICS) Security Dataset
The HAI dataset was collected from a realistic industrial control system (ICS) testbed augmented with a Hardware-In-the-Loop (HIL) simulator that emulates steam-turbine power generation and pumped-storage hydropower generation. 

Click [here](https://github.com/icsdataset/hai/blob/master/hai_dataset_technical_details_v3.0.pdf) to find out more about the HAI dataset.
> Please e-mail [us](mailto:haidataset@gmail.com?subject=[GitHub-HAI]%20) if you have any questions about the dataset.

## Contents
- [Background](#background)
- [HAI Testbed](#hai-testbed)
- [HAI Dataset](#hai-dataset)
- [Getting the Dataset](#getting-the-dataset)
- [Performance Metric](#performance-metric)
- [Projects using the Dataset](#projects-using-the-dataset)
- [Competitions](#competitions)
- [Contributors](#contributors)
- [Citation](#citation)


## Background
- In 2017, three laboratory-scale CPS testbeds were initially launched, namely GE’s turbine testbed, Emerson’s boiler testbed, and FESTO’s modular production system (MPS) water-treatment testbed. These testbeds are related to relatively simple processes, and were operated independently of each other.

- In 2018, a complex process system was built to combine the three systems using a HIL simulator, where the generation of thermal power and pumped-storage hydropower was simulated. This ensured that the variables were highly coupled and correlated for a richer dataset. In addition, an open platform communications united architecture (OPC-UA) gateway was installed to facilitate data collection from heterogeneous devices.

- The first version of HAI dataset, HAI 1.0,  was made available on GitHub and Kaggle in February 2020. This dataset included ICS operational data from normal and anomalous situations for 38 attacks. Subsequently, a debugged version of HAI 1.0, namely HAI 20.07, was released for the HAICon 2020 competition in August 2020.

- HAI 21.03 was released in 2021, and was based on a more tightly coupled HIL simulator to produce clearer attack effects with additional attacks. This version provides more quantitative information and covers a variety of operational situations, and provides better insights into the dynamic changes of the physical system.

- HAI 22.04 contained more sophisticated attacks that are significantly more difficult to detect than those in the previous versions. Comparing only the baseline TaPRs of HAICon 2020 and HAICon 2021, detection difficulty in HAI 22.04 is approximately four times higher than HAI 21.03.

- In 2022, HAI/HAIEnd 23.05 were developed for ICS endpoint threat detection. The HAIEnd dataset includes more points about the internal control logic of boiler's DCS. In addition, we provide Python NetworkX graph data that helps in analyzing and optimizing anomaly detection performance. Click [here](https://github.com/icsdataset/hai/tree/master/graph) to find out more about the NetworkX graphs.

## HAI Testbed
The testbed consists of four different processes: boiler process, turbine process, water treatment process and HIL simulation:

- **Boiler Process (P1):** This includes water-to-water heat transfer at a low pressure and a moderate temperature. This process is controlled using Emerson Ovation DCS.
- **Turbine Process (P2):** A rotor kit process that closely simulates the behavior of an actual rotating machine. It is controlled by GE's Mark VIe DCS.
- **Water Treatment Process (P3):** This process includes pumping water to the upper reservoir and releasing it back into the lower reservoir. It is controlled by Siemens's S7-300 PLC.
- **HIL Simulation(P4):** Both the boiler and turbine processes are interconnected to synchronize with the rotating speed of the virtual steam-turbine power generation model. 
The pump and value in the water-treatment process are controlled by the pumped-storage hydropower generation model.
The dSPACE's SCALEXIO system is used for the HIL simulations and is interconnected with the real-world processes through a Siemens S7-1500 PLC and ET200 remote IO devices for data-acquisition system based on the OPC gateway.


## HAI Dataset
Two major versions of HAI datasets have been released thus far. Each dataset consists of several CSV files, and each file satisfies time continuity. The quantitative summary of each version are as follows:
> **Note:** The **version numbering** follows a **date-based scheme**, where the version number indicates the released date of the HAI dataset.  HAI 20.07 is the bug-fixed version of HAI v1.0 released in February 2020.
<table align=center >
    <thead  align=center>
        <tr bgcolor='#bbbbbb'>
            <th rowspan=2>Version</th>
            <th rowspan=2>Data Points<br>(points/sec)</th>
            <th colspan=3>Normal Dataset </th>
            <th colspan=4>Attack Dataset</th>
        </tr>
         <tr>
            <th>Files<br>(CSV)</th>
            <th>Interval<br>(hours)</th>
            <th>Size<br>(MB)</th>
            <th>Files<br>(CSV)</th>
            <th>Attack Count</th>
            <th>Interval<br>(hours)</th>
            <th>Size<br>(MB)</th>
        </tr>
    </thead>
    <tbody>
        <tr bgcolor='#dddddd'>
            <td rowspan=5 align=right><a href="https://github.com/icsdataset/hai/tree/master/haiend-23.05"> HAI 23.05 <a> <br> <b> <a href="https://github.com/icsdataset/hai/tree/master/hai-23.05"> HAIEnd 23.05 <a></b> </td>
             <td align=right rowspan=5> 86<br><b>225</b></td>
             <td align=right>hai-train1<br><b>end-train1</b></td>
             <td align=right>78</td>
             <td align=right>154.9<br><b>250.5</b></td>
             <td align=right> hai-test1<br><b>end-test1</b></td>
             <td align=right>14</td>
             <td align=right>15</td>
             <td align=right>29.8<br><b>48.2</b></td>
          </tr>
          <tr >
             <td align=right> hai-train2<br><b>end-train2</b></td>
             <td align=right>81</td>
             <td align=right>161.3<br><b>260.7</b></td>
             <td align=right>hai-test2<br><b>end-test2</b></td>
             <td align=right>38</td>
             <td align=right>64</td>
             <td align=right>126.8<br><b>204.8</b></td>
        </tr>
        <tr bgcolor='#dddddd'>
             <td align=right> hai-train3<br><b>end-train3</b></td>
             <td align=right>35</td>
             <td align=right>69.4<br><b>112.7</b></td>
             <td rowspan=2 colspan=4> </td>
        </tr>
        <tr>
             <td align=right>hai-train4<br><b>end-train4</b></td>
             <td align=right>55</td>
             <td align=right>109.2<br><b>176.0</b></td>
        </tr>
        <tr >
            <td align=right> <b>Total</b></td>
            <td align=right><b>249</b></td>
            <td align=right>494.8<br><b>799.9</b></td>
            <td align=right><b>Total</td>
             <td align=right><b>52</b></td>
             <td align=right><b>79</b></td>
             <td align=right>156.6<br><b>253.0</b></td>
        </tr>   
          <tr bgcolor='#dddddd'>
            <td rowspan=7 align=center><b><a href="https://github.com/icsdataset/hai/tree/master/hai-22.04"> HAI 22.04<a></b> </td>
            <td rowspan=7 align=right >86</td>
            <td align=right> train1</td>
             <td align=right>26</td>
             <td align=right>50.7</td>
             <td align=right> test1</td>
             <td align=right>7</td>
             <td align=right>24</td>
             <td align=right>48.2</td>
          </tr>
          <tr >
             <td align=right>train2</td>
             <td align=right>56 </td>
             <td align=right>108.9</td>
             <td align=right>test2</td>
             <td align=right>17</td>
             <td align=right>23 </td>
             <td align=right>44.5</td>
        </tr>
        <tr bgcolor='#dddddd'>
             <td align=right>train3</td>
             <td align=right>35 </td>
             <td align=right>66.7</td>
             <td align=right>test3</td>
             <td align=right>10</td>
             <td align=right>17.3 </td>
             <td align=right>33.4</td>
        </tr>
        <tr>
             <td align=right>train4</td>
             <td align=right>24 </td>
             <td align=right>45.7</td>
             <td align=right>test4</td>
             <td align=right>24</td>
             <td align=right>36 </td>
             <td align=right>69.5</td>
        </tr>
        <tr bgcolor='#dddddd'> 
             <td align=right>train5</td>
             <td align=right>66 </td>
             <td align=right>125.6</td>
             <td rowspan=2 colspan=4> </td>
        </tr>
        <tr>
             <td align=right>train6</td>
             <td align=right>72 </td>
             <td align=right>136.8</td>
        </tr>       
        <tr >
            <td align=right> <b>Total</b></td>
            <td align=right> <b>279 </b></td>
            <td align=right><b>534.4</b></td>
            <td align=right><b>Total</td>
             <td align=right><b>58</b></td>
             <td align=right><b>100.3 </b></td>
             <td align=right><b>195.6</b></td>
        </tr>
        <tr bgcolor='#dddddd'>
            <td rowspan=6 align=center><b><a href="https://github.com/icsdataset/hai/tree/master/hai-21.03"> HAI 21.03<a></b> </td>
            <td rowspan=6 align=right > 78</td>
            <td align=right>train1</td>
             <td align=right>60 </td>
             <td align=right>100</td>
             <td align=right> test1</td>
             <td align=right>5</td>
             <td align=right>12 </td>
             <td align=right>22</td>
        </tr>
        <tr >
             <td align=right>train2</td>
             <td align=right>63 </td>
             <td align=right>116</td>
             <td align=right>test2</td>
             <td align=right>20</td>
             <td align=right>33 </td>
             <td align=right>62</td>
        </tr>
        <tr bgcolor='#dddddd'>
            <td align=right>train3</td>
             <td align=right>229</td>
             <td align=right>246</td>
             <td align=right>test3</td>
             <td align=right>8</td>
             <td align=right>30 </td>
             <td align=right>56</td>
        </tr>
        <tr>
            <td rowspan=2 colspan=3> </td>
             <td align=right>test4</td>
             <td align=right>5</td>
             <td align=right>11 </td>
             <td align=right>20</td>
        </tr>
          <tr bgcolor='#dddddd'>
             <td align=right>test5</td>
             <td align=right>12</td>
             <td align=right>26 </td>
             <td align=right>48</td>
        </tr>
        <tr >
            <td align=right> <b>Total</b></td>
            <td align=right> <b>352 </b></td>
            <td align=right><b>471</b></td>
            <td align=right><b>Total</td>
             <td align=right><b>50</b></td>
             <td align=right><b>112 </b></td>
             <td align=right><b>205</b></td>
        </tr>
        <tr >
            <td rowspan=3 align=center> <b><a href="https://github.com/icsdataset/hai/tree/master/hai-20.07"> HAI 20.07<a> </b><br> (HAI1.0)</td>
            <td rowspan=3 align=right > 59</td>
            <td align=right>train1</td>
             <td align=right>86</td>
             <td align=right>127</td>
             <td align=right>test1</td>
             <td align=right>28</td>
             <td align=right>81</td>
             <td align=right>119</td>
        </tr>
           <tr bgcolor='#dddddd'>
            <td align=right>train1</td>
             <td align=right>91</td>
             <td align=right>98</td>
             <td align=right>test1</td>
             <td align=right>10</td>
             <td align=right>42 </td>
             <td align=right>62</td>
        </tr>
           <tr >
            <td align=right> <b>Total</b></td>
            <td align=right> <b>177</b></td>
            <td align=right><b>225</b></td>
            <td align=right><b>Total</td>
             <td align=right><b>38</b></td>
             <td align=right><b>123 </b></td>
             <td align=right><b>181</b></td>
                </tr>
    </tbody>
</table>

                
### Data fields 
                
The time-series data in each CSV file satisfies time continuity. The first column represents the observed time in the “yyyy-MM-dd hh:mm:ss” format, while the rest of the columns provide the recorded SCADA data points. 
The last four columns provide data labels for whether an attack occurred 
                . 
Out of these four columns, the attack column is applicable to all the process and the other three columns are applicable to the corresponding control processes.         
                
> Refer to the **latest technical manual** for the details for each column.
                
> From the HAI 22.04 version, attack labels for each process (attack_p1, attack_p2, attack p3) have been excluded. This is because they can be replaced by the attack targets (controllers and points) provided for each dataset version.
                
<div align="center">
    
| time                  |P1_B2004        | P2_B2016| ...  | P4_HT_LD  | attack   | attack_P1   |    ...          | attack_P3 |
|:---:                  | :---:           |  :---:  |  :---: |  :---:  |  :---:   |   :---:     |  :---:         | :---:   |
|20190926 13:00:00| 0.09830         |1.07370       | ...   |  0       |  0    |   0       |    ...      | 0   |
|20190926 13:00:01| 0.09830        | 1.07410      | ...   |  0       |  1     |   0       |    ...      | 1  |
|20190926 13:00:02| 0.09830        | 1.07380        | ...   |  0       |  1     |   0       |    ...      | 1   |
|20190926 13:00:03| 0.09830        | 1.07360       | ...   |  0       |  1     |   1       |    ...      | 1   |
|20190926 13:00:04| 0.09830         | 1.07430        | ...   |  0       |  1     |  1      |    ...      | 1 |
                
</div>

## Getting the dataset
Type ```git clone```, and the paste the below URL. 
```
$ git clone https://github.com/icsdataset/hai
```
To unzip multiple gzip files, you can use:
```
$ gunzip *.gz
```
From HAI 22.04, use ```git lfs pull``` to download the actual file contents managed by [Git LFS](https://git-lfs.com/).
```
$ git lfs pull
```
                
## Performance Metric
The use of [eTaPR (Enhanced Time-series Aware Precision and Recall)](https://github.com/saurf4ng/eTaPR) metric is strongly recommended to evaluate your anomaly detection model, which provides fairness to performance comparisons with other studies. Got something to suggest? [Let us know!](mailto:haidataset@gmail.com?subject=[GitHub-eTaPR]%20)

## Projects using the dataset
Here are some projects and experiments that are using or featuring the dataset in interesting ways. Got something to add? [Let us know!](mailto:haidataset@gmail.com?subject=[GitHub-Share]%20)

The related projects so far are as follows.
### Year 2023
01. [A Comparative Study of Time Series Anomaly Detection Models for Industrial Control Systems][AD_23_01]
02. [CPS-GUARD: Intrusion detection for cyber-physical systems and IoT devices using outlier-aware deep autoencoders][AD_23_02]
03. [Detection of Cyberattacks and Anomalies in Cyber-Physical Systems: Approaches, Data Sources, Evaluation][AD_23_03]
04. [Machine learning in industrial control system (ICS) security: current landscape, opportunities and challenges][AD_23_04]
05. [Monitoring industrial control systems via spatio-temporal graph neural networks][AD_23_05]  
06. [Time-series Anomaly Detection via Contextual Discriminative Contrastive Learning][AD_23_06] 
                
### Year 2022 
01. [A Hybrid Algorithm Incorporating Vector Quantization and One-Class Support Vector Machine for industrial Anomaly Detection][AD_22_01]
02. [Anomalous behaviour detection for cyber defence in modern industrial control systems][AD_22_02]
03. [Benchmarking machine learning based detection of cyber attacks for critical infrastructure][AD_22_03]
04. [Can Industrial Intrusion Detection Be SIMPLE?][AD_22_04]
05. [Deep Analysis Net with Causal Embedding for Coal-fired power plant Fault Detection and Diagnosis (DANCE4CFDD)][AD_22_05] 
06. [Frequency-Based Representation of Massive Alerts and Combination of Indicators by Heterogeneous Intrusion Detection Systems for Anomaly Detection][AD_22_06]
07. [Improving Method of Anomaly Detection Performance for Industrial IoT Environment][AD_22_07]
08. [IPAL: breaking up silos of protocol-dependent and domain-specific industrial intrusion detection systems][AD_22_08]
09. [Learning Sparse Latent Graph Representations for Anomaly Detection in Multivariate Time Series][AD_22_09]
10. [Mad: Self-supervised masked anomaly detection task for multivariate time series][AD_22_10]
11. [Multivariate Time Series Anomaly Detection with Few Positive Samples][AD_22_11]
12. [Residual size is not enough for anomaly detection: improving detection performance using residual similarity in multivariate time series][AD_22_12]
13. [Towards building intrusion detection systems for multivariate time-series data][AD_22_13]
14. [Variational restricted Boltzmann machines to automated anomaly detection][AD_22_14]

### Year 2021
01. [Research on improvement of anomaly detection performance in industrial control systems][AD_21_10]
02. [E-sfd: Explainable sensor fault detection in the ics anomaly detection system][AD_21_09]
03. [Stacked-autoencoder based anomaly detection with industrial control system][AD_21_08]
04. [Improved mitigation of cyber threats in iiot for smart cities: A new-era approach and scheme][AD_21_07]
06. [Revitalizing self-organizing map: Anomaly detection using forecasting error patterns][AD_21_04]
07. [Cluster-based deep one-class classification model for anomaly detection][AD_21_03]
08. [Measurement data intrusion detection in industrial control systems based on unsupervised learning][AD_21_02]
09. [A machine learning approach for anomaly detection in industrial control systems based on measurement data][AD_21_01]
10. [Probabilistic attack sequence generation and execution based on mitre att&ck for ics datasets][TB_21_01]
                
### Year 2020
01. [Anomaly detection in time-series data environment][AD_20_02]
02. [Detecting anomalies in time-series data using unsupervised learning and analysis on infrequent signatures][AD_20_01]
03. [Expansion of ICS testbed for security validation based on MITRE ATT&CK techniques][TB_20_01] 
04. [Expanding a programmable cps testbed for network attack analysis][TB_20_02]
05. [Co-occurrence based security event analysis and visualization for cyber physical systems][TB_20_03]
06. [Expansion of ICS testbed for security validation based on MITRE ATT&CK techniques][TB_20_01] 
07. [Expanding a programmable cps testbed for network attack analysis][TB_20_02]
08. [Co-occurrence based security event analysis and visualization for cyber physical systems][TB_20_03]
               
[AD_23_01]: https://doi.org/10.3390/s23031310
[AD_23_02]: https://doi.org/10.1016/j.cose.2023.103210
[AD_23_03]: https://doi.org/10.3390/a16020085
[AD_23_04]: https://doi.org/10.1007/s10844-022-00753-1
[AD_23_05]: https://doi.org/10.1016/j.engappai.2023.106144
[AD_23_06]: https://doi.org/10.48550/arXiv.2304.07898
                
[AD_22_01]: https://doi.org/10.1109/TII.2022.3145834        
[AD_22_02]: http://hdl.handle.net/2436/625131
[AD_22_03]: https://doi.org/10.1109/ICOIN53446.2022.9687293
[AD_22_04]: https://doi.org/10.1007/978-3-031-17143-7_28
[AD_22_05]: https://doi.org/10.2172/1844966
[AD_22_06]: https://doi.org/10.3390/s22124417
[AD_22_07]: https://doi.org/10.32604/cmc.2022.026619
[AD_22_08]: https://doi.org/10.1145/3545948.3545968
[AD_22_09]: https://doi.org/10.1145/3534678.3539117
[AD_22_10]: https://doi.org/10.1109/IJCNN55064.2022.9892218
[AD_22_11]: https://doi.org/10.1109/IJCNN55064.2022.9892091
[AD_22_12]: https://doi.org/10.1145/3477314.3506990
[AD_22_13]: https://doi.org/10.1007/978-3-030-96057-5_4
[AD_22_14]: https://doi.org/10.1007/s00521-022-07060-4
                
[AD_21_10]: https://link.springer.com/chapter/10.1007/978-3-030-89432-0_7
[AD_21_09]: https://ieeexplore.ieee.org/document/9568906
[AD_21_08]: https://www.scirp.org/journal/paperinformation.aspx?paperid=106463
[AD_21_07]: https://www.mdpi.com/1424-8220/21/6/1976
[AD_21_06]: https://link.springer.com/chapter/10.1007/978-3-030-96057-5_4

[AD_21_04]: https://link.springer.com/chapter/10.1007/978-3-030-78120-0_25
[AD_21_03]: https://jit.ndhu.edu.tw/article/view/2553
[AD_21_02]: https://www.aimspress.com/article/doi/10.3934/aci.2021004
[AD_21_01]: https://www.mdpi.com/2079-9292/10/4/407
[TB_21_01]: https://dl.acm.org/doi/abs/10.1145/3474718.3474722 "CSET 2021"  
                
[AD_20_02]: https://dl.acm.org/doi/abs/10.1145/3440943.3444353
[AD_20_01]: https://www.koreascience.or.kr/article/JAKO202009252091939.page
[TB_20_01]: https://www.usenix.org/conference/cset20/presentation/choi "CSET 2020"
[TB_20_02]: https://dl.acm.org/doi/abs/10.1145/3320269.3405447 "Asis CCS 2020"
[TB_20_03]: https://link.springer.com/chapter/10.1007/978-3-030-50732-9_70 "HCI 2020"
         
                
## Competitions 
Since 2020, we have held two AI competitions using the HAI dataset. The competition website shares the competition baseline codes and the winner's codes.
 * [HAICon 2020][haicon2020] with HAI 21.03
 * [HAICon 2021][haicon2021] with HAI 22.04
        
[haicon2020]:  https://dacon.io/competitions/official/235624/overview/description
[haicon2021]:  https://dacon.io/en/competitions/official/235757/overview/description      
                
## Contributors
[Shin, Hyeok-Ki][shk_gs]; [Lee, Woomyo][lwm_acm]; [Choi, Seungoh][cso_gs]; [Hwang, Won-Seok][hws_gs] ; [Yun, Jeong-Han][yjh_gs] ; [Min, Byung-Gil][mbg_acm]; [Kim, HyoungChun][khc_acm] 
                
The Affiliated Institute of ETRI, Daejeon, South Korea.
                
                
[shk_gs]: https://scholar.google.com/citations?hl=ko&user=oKTla4QAAAAJ 
[lwm_acm]: https://dl.acm.org/profile/99659273937
[cso_gs]: https://scholar.google.com/citations?hl=ko&user=BW1uvqIAAAAJ
[hws_gs]: https://scholar.google.com/citations?user=v9LE7JYAAAAJ&hl=ko
[yjh_gs]: https://scholar.google.com/citations?hl=ko&user=X8FNSdkAAAAJ
[mbg_acm]: https://dl.acm.org/profile/99659015490
[khc_acm]: https://dl.acm.org/profile/81367593748
                
## License
This work is licensed under a [Creative Commons Attribution-ShareAlike License (CC BY-SA 4.0)](http://creativecommons.org/licenses/by-sa/4.0/).

## Citation
If you publish your works that use HAI data sets, HAICon competitions, and eTaPR, please cite the sources below:             
### HAI 22.04, HAI 23.05, HAIEnd 23.5
```bibtex
  @misc{github,
    author={Shin,  Hyeok-Ki; Lee, Woomyo; Choi, Seungoh; Yun, Jeong-Han; and Min, Byung-Gi},
    title={HAI security datasets},
    year={2023},
    url={https://github.com/icsdataset/hai},
 }
```
### HAI 21.03, HAICon 2020, HAICon 2021
```bibtex
    @inproceedings{10.1145/3474718.3474719,
    author = {Shin,  Hyeok-Ki; Lee, Woomyo; Yun, Jeong-Han; and Min, Byung-Gi},
    title = {Two ICS Security Datasets and Anomaly Detection Contest on the HIL-Based Augmented ICS Testbed},
    year = {2021},
    isbn = {9781450390651},
    publisher = {Association for Computing Machinery},
    address = {New York, NY, USA},
    url = {https://doi.org/10.1145/3474718.3474719},
    doi = {10.1145/3474718.3474719},
    abstract = {Security datasets with various operating characteristics and abnormal situations of industrial control system (ICS) are essential to develop artificial intelligence (AI)-based control system security technology. In this study, we built a hardware-in-the-loop (HIL)-based augmented ICS (HAI) testbed and developed ICS security datasets. Here, we introduce the second dataset (HAI 21.03), which was developed with the user feedback of the first released version (HAI 20.07). All HAI datasets are publicly available at https://github.com/icsdataset/hai. HAI 21.03 was expanded by adding data points and normal/attack scenarios to HAI 20.07. We also held an AI-based anomaly detection contest (HAICon 2020) utilizing the HAI datasets developed so far, giving many AI researchers an opportunity to discuss and share ideas for ICS anomaly detection research. This paper presents the results of the HAICon 2020. The results of the top teams in the competition can be used as a performance comparison criterion when using HAI 21.03. },
    booktitle = {Cyber Security Experimentation and Test Workshop},
    pages = {36–40},
    numpages = {5},
    keywords = {security dataset, testbed, artificial intelligence, hardware-in-the-loop, industrial control system, anomaly detection},
    location = {Virtual, CA, USA},
    series = {CSET '21}
}
```
                
### HAI 20.07
```bibtex
@inbook{10.5555/3485754.3485755,
    author = {Shin, Hyeok-Ki; Lee, Woomyo; Yun, Jeong-Han; and Kim, HyoungChun},
    title = {HAI 1.0: HIL-Based Augmented ICS Security Dataset},
    year = {2020},
    publisher = {USENIX Association},
    address = {USA},
    abstract = {Datasets are paramount to the development of AI-based technologies. However, the available cyber-physical system (CPS) datasets are insufficient. In this paper, we introduce the HIL-based augmented ICS security (HAI) dataset 1.0 (https://github.com/icsdataset/hai), the first CPS dataset collected using the HAI testbed. The HAI testbed comprises three physical control systems, namely GE turbine, Emerson boiler, and FESTO water treatment systems, combined through a dSPACE hardware-in-the-loop (HIL) simulator. We built an environment to remotely and automatically manipulate all components of a feedback control loop. Using this environment, we collected the HAI dataset 1.0 while repeatedly running a large number of benign and malicious scenarios for a long period with minimal human effort. We will continue to improve the HAI testbed and release new versions of the HAI dataset.},
    booktitle = {Proceedings of the 13th USENIX Conference on Cyber Security Experimentation and Test},
    articleno = {1},
    numpages = {1}
}
```
                        
### eTaPR
```bibtex
@inproceedings{ 
    10.1145/3477314.3507024,
    author = {Hwang, Won-Seok; Yun, Jeong-Han; Kim, Jonguk; and Min, Byung Gil},
    title = {"Do You Know Existing Accuracy Metrics Overrate Time-Series Anomaly Detections?"},
    year = {2022},
    isbn = {9781450387132},
    publisher = {Association for Computing Machinery},
    address = {New York, NY, USA},
    url = {https://doi.org/10.1145/3477314.3507024},
    doi = {10.1145/3477314.3507024},
    booktitle = {Proceedings of the 37th ACM/SIGAPP Symposium on Applied Computing},
    pages = {403–412},
    numpages = {10},
    location = {Virtual Event},
    series = {SAC '22}
}
```
                
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
    <td>keywords</td>
    <td><code itemprop="keywords">ICS, CPS, AI Dataset, Anomaly Detection</code></td>
  </tr>
  <tr>
    <td>alternateName</td>
    <td><code itemprop="alternateName">HAI, HAIEnd</code></td>
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
    <td><code itemprop="description">The HAI security dataset was collected from a realistic Industrial Control System (ICS) testbed augmented with a Hardware-In-the-Loop (HIL) simulator that emulates steam-turbine power generation and pumped-storage hydropower generation.</code></td>
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
        <td>
       <code itemprop="citation">https://dl.acm.org/doi/abs/10.1145/3474718.3474719</code>
       <code itemprop="citation">https://dl.acm.org/doi/abs/10.5555/3485754.3485755</code>
       <code itemprop="citation">https://dl.acm.org/doi/10.1145/3357384.3358118</code>
       </td>
  </tr>
</table>
</div>
