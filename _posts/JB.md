```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import plotly.express as px
import koreanize_matplotlib
```


```python
import numpy as np
```


```python
%config InlineBackend.figure_format = 'retina'
```


```python
from matplotlib import rc
rc('font',family='AppleGothic')
```


```python
fis = pd.read_excel('FISIS_MulipleTable_201703-202209.xls')
fis 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>복수 통계표 조회결과_201703~202209</th>
      <th>Unnamed: 1</th>
      <th>Unnamed: 2</th>
      <th>Unnamed: 3</th>
      <th>Unnamed: 4</th>
      <th>Unnamed: 5</th>
      <th>Unnamed: 6</th>
      <th>Unnamed: 7</th>
      <th>Unnamed: 8</th>
      <th>Unnamed: 9</th>
      <th>...</th>
      <th>Unnamed: 20</th>
      <th>Unnamed: 21</th>
      <th>Unnamed: 22</th>
      <th>Unnamed: 23</th>
      <th>Unnamed: 24</th>
      <th>Unnamed: 25</th>
      <th>Unnamed: 26</th>
      <th>Unnamed: 27</th>
      <th>Unnamed: 28</th>
      <th>Unnamed: 29</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>회사명</td>
      <td>회사코드</td>
      <td>보고서명</td>
      <td>보고서코드</td>
      <td>항목</td>
      <td>factor_id</td>
      <td>단위</td>
      <td>2017년03월</td>
      <td>2017년06월</td>
      <td>2017년09월</td>
      <td>...</td>
      <td>2020년06월</td>
      <td>2020년09월</td>
      <td>2020년12월</td>
      <td>2021년03월</td>
      <td>2021년06월</td>
      <td>2021년09월</td>
      <td>2021년12월</td>
      <td>2022년03월</td>
      <td>2022년06월</td>
      <td>2022년09월</td>
    </tr>
    <tr>
      <th>1</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유동성(유동성)</td>
      <td>SDSA018V</td>
      <td>업무용고정자산비율</td>
      <td>F000001222</td>
      <td>%</td>
      <td>12.7</td>
      <td>12.76</td>
      <td>12.53</td>
      <td>...</td>
      <td>11.74</td>
      <td>11.4</td>
      <td>11.73</td>
      <td>11.71</td>
      <td>11.5</td>
      <td>11.1</td>
      <td>11.51</td>
      <td>11.57</td>
      <td>11.4</td>
      <td>11.62</td>
    </tr>
    <tr>
      <th>2</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유동성(유동성)</td>
      <td>SDSA018V</td>
      <td>업무용고정자산비율_업무용고정자산</td>
      <td>F000001223</td>
      <td>백만원</td>
      <td>183788</td>
      <td>186087</td>
      <td>185995</td>
      <td>...</td>
      <td>193869</td>
      <td>193339</td>
      <td>194340</td>
      <td>193950</td>
      <td>194355</td>
      <td>192903</td>
      <td>198118</td>
      <td>197763</td>
      <td>198510</td>
      <td>199784</td>
    </tr>
    <tr>
      <th>3</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유동성(유동성)</td>
      <td>SDSA018V</td>
      <td>업무용고정자산비율_자기자본</td>
      <td>F000001224</td>
      <td>백만원</td>
      <td>1446700</td>
      <td>1458425</td>
      <td>1483941</td>
      <td>...</td>
      <td>1651703</td>
      <td>1695743</td>
      <td>1656133</td>
      <td>1656609</td>
      <td>1689394</td>
      <td>1737130</td>
      <td>1721471</td>
      <td>1709598</td>
      <td>1741688</td>
      <td>1719616</td>
    </tr>
    <tr>
      <th>4</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유동성(유동성)</td>
      <td>SDSA018V</td>
      <td>유동성커버리지비율</td>
      <td>F000001225</td>
      <td>%</td>
      <td>123.22</td>
      <td>126.75</td>
      <td>109.89</td>
      <td>...</td>
      <td>104.28</td>
      <td>105.5</td>
      <td>102.4</td>
      <td>109.09</td>
      <td>105.61</td>
      <td>106.03</td>
      <td>111.44</td>
      <td>113.39</td>
      <td>123.69</td>
      <td>117.46</td>
    </tr>
    <tr>
      <th>5</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유동성(유동성)</td>
      <td>SDSA018V</td>
      <td>유동성커버리지비율_총 고유동성자산</td>
      <td>F000001226</td>
      <td>백만원</td>
      <td>1899934</td>
      <td>2014544</td>
      <td>2146704</td>
      <td>...</td>
      <td>2170533</td>
      <td>2336699</td>
      <td>2291540</td>
      <td>2269091</td>
      <td>2266289</td>
      <td>2488655</td>
      <td>2722469</td>
      <td>2958848</td>
      <td>2761502</td>
      <td>3052585</td>
    </tr>
    <tr>
      <th>6</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유동성(유동성)</td>
      <td>SDSA018V</td>
      <td>유동성커버리지비율_순현금유출액</td>
      <td>F000001227</td>
      <td>백만원</td>
      <td>1541845</td>
      <td>1589359</td>
      <td>1953446</td>
      <td>...</td>
      <td>2081465</td>
      <td>2214942</td>
      <td>2237740</td>
      <td>2079978</td>
      <td>2145982</td>
      <td>2347067</td>
      <td>2442978</td>
      <td>2609542</td>
      <td>2232686</td>
      <td>2598757</td>
    </tr>
    <tr>
      <th>7</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유동성(유동성)</td>
      <td>SDSA018V</td>
      <td>순안정자금조달비율</td>
      <td>F000001231</td>
      <td>%</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>103.98</td>
      <td>105.09</td>
      <td>105.94</td>
      <td>106.21</td>
      <td>109.66</td>
      <td>104.39</td>
      <td>106.55</td>
      <td>105.25</td>
      <td>103.78</td>
      <td>102.1</td>
    </tr>
    <tr>
      <th>8</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유동성(유동성)</td>
      <td>SDSA018V</td>
      <td>순안정자금조달비율_안정자금가용금액</td>
      <td>F000001232</td>
      <td>백만원</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>11000429</td>
      <td>11138752</td>
      <td>11420823</td>
      <td>11592445</td>
      <td>11927730</td>
      <td>11867790</td>
      <td>12555113</td>
      <td>12838159</td>
      <td>12936635</td>
      <td>13431628</td>
    </tr>
    <tr>
      <th>9</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유동성(유동성)</td>
      <td>SDSA018V</td>
      <td>순안정자금조달비율_안정자금조달필요금액</td>
      <td>F000001233</td>
      <td>백만원</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>10579465</td>
      <td>10599740</td>
      <td>10780947</td>
      <td>10914862</td>
      <td>10877396</td>
      <td>11368841</td>
      <td>11782987</td>
      <td>12197727</td>
      <td>12465537</td>
      <td>13154757</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 30 columns</p>
</div>




```python
# 중장기 유동성 비율 NSFR
# 고유동성자산(1년 단위) ÷ 순현금유출(1년 단위)
# 유동성커버리지 비율 LCR
고유동성자산 = fis.iloc[5,:]
순현금유출 = fis.iloc[6,:]
순안정자금조달비율 = fis.iloc[7,:]
유동성커버리지비율= fis.iloc[4,7:]
NSFR = pd.concat([fis.iloc[0,:],고유동성자산,순현금유출,순안정자금조달비율,유동성커버리지비율], ignore_index=True,axis=1)
NSFR = NSFR.set_index(NSFR[0])
NSFR = NSFR.drop(0,axis=1)
NSFR
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
    <tr>
      <th>0</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>회사명</th>
      <td>전북은행</td>
      <td>전북은행</td>
      <td>전북은행</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>회사코드</th>
      <td>0010022</td>
      <td>0010022</td>
      <td>0010022</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>보고서명</th>
      <td>유동성(유동성)</td>
      <td>유동성(유동성)</td>
      <td>유동성(유동성)</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>보고서코드</th>
      <td>SDSA018V</td>
      <td>SDSA018V</td>
      <td>SDSA018V</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>항목</th>
      <td>유동성커버리지비율_총 고유동성자산</td>
      <td>유동성커버리지비율_순현금유출액</td>
      <td>순안정자금조달비율</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>factor_id</th>
      <td>F000001226</td>
      <td>F000001227</td>
      <td>F000001231</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>단위</th>
      <td>백만원</td>
      <td>백만원</td>
      <td>%</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2017년03월</th>
      <td>1899934</td>
      <td>1541845</td>
      <td>NaN</td>
      <td>123.22</td>
    </tr>
    <tr>
      <th>2017년06월</th>
      <td>2014544</td>
      <td>1589359</td>
      <td>NaN</td>
      <td>126.75</td>
    </tr>
    <tr>
      <th>2017년09월</th>
      <td>2146704</td>
      <td>1953446</td>
      <td>NaN</td>
      <td>109.89</td>
    </tr>
    <tr>
      <th>2017년12월</th>
      <td>2221235</td>
      <td>2139108</td>
      <td>NaN</td>
      <td>103.84</td>
    </tr>
    <tr>
      <th>2018년03월</th>
      <td>2099805</td>
      <td>1932949</td>
      <td>111.49</td>
      <td>108.63</td>
    </tr>
    <tr>
      <th>2018년06월</th>
      <td>2210747</td>
      <td>2141616</td>
      <td>112.14</td>
      <td>103.23</td>
    </tr>
    <tr>
      <th>2018년09월</th>
      <td>2152376</td>
      <td>1855382</td>
      <td>110.77</td>
      <td>116.01</td>
    </tr>
    <tr>
      <th>2018년12월</th>
      <td>2066364</td>
      <td>1865480</td>
      <td>110.71</td>
      <td>110.77</td>
    </tr>
    <tr>
      <th>2019년03월</th>
      <td>1945224</td>
      <td>1746519</td>
      <td>111.36</td>
      <td>111.38</td>
    </tr>
    <tr>
      <th>2019년06월</th>
      <td>2122067</td>
      <td>1963055</td>
      <td>112.6</td>
      <td>108.1</td>
    </tr>
    <tr>
      <th>2019년09월</th>
      <td>2070408</td>
      <td>1789174</td>
      <td>106.38</td>
      <td>115.72</td>
    </tr>
    <tr>
      <th>2019년12월</th>
      <td>2141579</td>
      <td>1899757</td>
      <td>108.11</td>
      <td>112.73</td>
    </tr>
    <tr>
      <th>2020년03월</th>
      <td>2088486</td>
      <td>1789109</td>
      <td>108.25</td>
      <td>116.73</td>
    </tr>
    <tr>
      <th>2020년06월</th>
      <td>2170533</td>
      <td>2081465</td>
      <td>103.98</td>
      <td>104.28</td>
    </tr>
    <tr>
      <th>2020년09월</th>
      <td>2336699</td>
      <td>2214942</td>
      <td>105.09</td>
      <td>105.5</td>
    </tr>
    <tr>
      <th>2020년12월</th>
      <td>2291540</td>
      <td>2237740</td>
      <td>105.94</td>
      <td>102.4</td>
    </tr>
    <tr>
      <th>2021년03월</th>
      <td>2269091</td>
      <td>2079978</td>
      <td>106.21</td>
      <td>109.09</td>
    </tr>
    <tr>
      <th>2021년06월</th>
      <td>2266289</td>
      <td>2145982</td>
      <td>109.66</td>
      <td>105.61</td>
    </tr>
    <tr>
      <th>2021년09월</th>
      <td>2488655</td>
      <td>2347067</td>
      <td>104.39</td>
      <td>106.03</td>
    </tr>
    <tr>
      <th>2021년12월</th>
      <td>2722469</td>
      <td>2442978</td>
      <td>106.55</td>
      <td>111.44</td>
    </tr>
    <tr>
      <th>2022년03월</th>
      <td>2958848</td>
      <td>2609542</td>
      <td>105.25</td>
      <td>113.39</td>
    </tr>
    <tr>
      <th>2022년06월</th>
      <td>2761502</td>
      <td>2232686</td>
      <td>103.78</td>
      <td>123.69</td>
    </tr>
    <tr>
      <th>2022년09월</th>
      <td>3052585</td>
      <td>2598757</td>
      <td>102.1</td>
      <td>117.46</td>
    </tr>
  </tbody>
</table>
</div>




```python
NSFR.columns
```




    RangeIndex(start=1, stop=5, step=1)



## 총 고유동성자산/ 순현금유출액 /순안정자금조달비율/	유동성커버리지비율


```python
NSFR = NSFR.rename(columns={ 1:"총 고유동성자산",2:'순현금유출액',3:'순안정자금조달비율',4:'유동성커버리지비율'})
NSFR = NSFR.fillna(0)
NSFR = NSFR.iloc[7:,]
NSFR = NSFR.astype(int)
NSFR
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>총 고유동성자산</th>
      <th>순현금유출액</th>
      <th>순안정자금조달비율</th>
      <th>유동성커버리지비율</th>
    </tr>
    <tr>
      <th>0</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017년03월</th>
      <td>1899934</td>
      <td>1541845</td>
      <td>0</td>
      <td>123</td>
    </tr>
    <tr>
      <th>2017년06월</th>
      <td>2014544</td>
      <td>1589359</td>
      <td>0</td>
      <td>126</td>
    </tr>
    <tr>
      <th>2017년09월</th>
      <td>2146704</td>
      <td>1953446</td>
      <td>0</td>
      <td>109</td>
    </tr>
    <tr>
      <th>2017년12월</th>
      <td>2221235</td>
      <td>2139108</td>
      <td>0</td>
      <td>103</td>
    </tr>
    <tr>
      <th>2018년03월</th>
      <td>2099805</td>
      <td>1932949</td>
      <td>111</td>
      <td>108</td>
    </tr>
    <tr>
      <th>2018년06월</th>
      <td>2210747</td>
      <td>2141616</td>
      <td>112</td>
      <td>103</td>
    </tr>
    <tr>
      <th>2018년09월</th>
      <td>2152376</td>
      <td>1855382</td>
      <td>110</td>
      <td>116</td>
    </tr>
    <tr>
      <th>2018년12월</th>
      <td>2066364</td>
      <td>1865480</td>
      <td>110</td>
      <td>110</td>
    </tr>
    <tr>
      <th>2019년03월</th>
      <td>1945224</td>
      <td>1746519</td>
      <td>111</td>
      <td>111</td>
    </tr>
    <tr>
      <th>2019년06월</th>
      <td>2122067</td>
      <td>1963055</td>
      <td>112</td>
      <td>108</td>
    </tr>
    <tr>
      <th>2019년09월</th>
      <td>2070408</td>
      <td>1789174</td>
      <td>106</td>
      <td>115</td>
    </tr>
    <tr>
      <th>2019년12월</th>
      <td>2141579</td>
      <td>1899757</td>
      <td>108</td>
      <td>112</td>
    </tr>
    <tr>
      <th>2020년03월</th>
      <td>2088486</td>
      <td>1789109</td>
      <td>108</td>
      <td>116</td>
    </tr>
    <tr>
      <th>2020년06월</th>
      <td>2170533</td>
      <td>2081465</td>
      <td>103</td>
      <td>104</td>
    </tr>
    <tr>
      <th>2020년09월</th>
      <td>2336699</td>
      <td>2214942</td>
      <td>105</td>
      <td>105</td>
    </tr>
    <tr>
      <th>2020년12월</th>
      <td>2291540</td>
      <td>2237740</td>
      <td>105</td>
      <td>102</td>
    </tr>
    <tr>
      <th>2021년03월</th>
      <td>2269091</td>
      <td>2079978</td>
      <td>106</td>
      <td>109</td>
    </tr>
    <tr>
      <th>2021년06월</th>
      <td>2266289</td>
      <td>2145982</td>
      <td>109</td>
      <td>105</td>
    </tr>
    <tr>
      <th>2021년09월</th>
      <td>2488655</td>
      <td>2347067</td>
      <td>104</td>
      <td>106</td>
    </tr>
    <tr>
      <th>2021년12월</th>
      <td>2722469</td>
      <td>2442978</td>
      <td>106</td>
      <td>111</td>
    </tr>
    <tr>
      <th>2022년03월</th>
      <td>2958848</td>
      <td>2609542</td>
      <td>105</td>
      <td>113</td>
    </tr>
    <tr>
      <th>2022년06월</th>
      <td>2761502</td>
      <td>2232686</td>
      <td>103</td>
      <td>123</td>
    </tr>
    <tr>
      <th>2022년09월</th>
      <td>3052585</td>
      <td>2598757</td>
      <td>102</td>
      <td>117</td>
    </tr>
  </tbody>
</table>
</div>




```python
## 유동성 커버리지 비율 과 순안정자금조달비율 비교
plt.figure(figsize=(25,5))
plt.plot(NSFR[['순안정자금조달비율','유동성커버리지비율']],lw=3)

plt.legend(NSFR.columns[2:],fontsize=20)
plt.show()

```


    
![png](output_9_0.png)
    



```python
## 총 고유동성자산	순현금유출액	순안정자금조달비율	유동성커버리지비율 비교
## 중장기 유동성 비율 NSFR= 고유동성자산(1년 단위) ÷ 순현금유출(1년 단위)
fig, ax1 = plt.subplots(figsize=(20,8))
plt.grid(True)
ax1.plot( NSFR[['총 고유동성자산','순현금유출액']],'--')
# ax2는 y2에 대한 그래프
ax2 = ax1.twinx()
ax2.plot( NSFR['순안정자금조달비율'],color='g',lw=3)
ax2.plot( NSFR['유동성커버리지비율'],color='magenta',lw=3)
plt.legend(NSFR.columns,fontsize=20,loc = 'lower right')
plt.show()
```


    
![png](output_10_0.png)
    


## 고정이하여신 / 대손충당금적립비율 / 연체율


```python
fis2 = pd.read_excel('fis2.xls',header=0,index_col=4)
fis2 = fis2.T.set_index(['항목']).iloc[6:,:]
fis2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>기업여신:고정이하여신</th>
      <th>기업여신_대기업:고정이하여신</th>
      <th>기업여신_중소기업:고정이하여신</th>
      <th>대손충당금적립비율(고정이하여신대비)</th>
      <th>기업대출_연체율</th>
      <th>기업대출_대기업대출_연체율</th>
      <th>기업대출_중소기업대출_연체율</th>
    </tr>
    <tr>
      <th>항목</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017년03월</th>
      <td>115811</td>
      <td>9833</td>
      <td>105976</td>
      <td>45.84</td>
      <td>1.51</td>
      <td>1.49</td>
      <td>1.51</td>
    </tr>
    <tr>
      <th>2017년06월</th>
      <td>110552</td>
      <td>9834</td>
      <td>100718</td>
      <td>46.4</td>
      <td>1.43</td>
      <td>1.65</td>
      <td>1.41</td>
    </tr>
    <tr>
      <th>2017년09월</th>
      <td>93609</td>
      <td>9833</td>
      <td>83776</td>
      <td>47.34</td>
      <td>1.25</td>
      <td>1.71</td>
      <td>1.21</td>
    </tr>
    <tr>
      <th>2017년12월</th>
      <td>95324</td>
      <td>9833</td>
      <td>85490</td>
      <td>44.11</td>
      <td>1.22</td>
      <td>1.76</td>
      <td>1.17</td>
    </tr>
    <tr>
      <th>2018년03월</th>
      <td>91132</td>
      <td>9833</td>
      <td>81298</td>
      <td>59.71</td>
      <td>1.21</td>
      <td>2.04</td>
      <td>1.15</td>
    </tr>
    <tr>
      <th>2018년06월</th>
      <td>95088</td>
      <td>9827</td>
      <td>85263</td>
      <td>55.7</td>
      <td>1.29</td>
      <td>2.64</td>
      <td>1.22</td>
    </tr>
    <tr>
      <th>2018년09월</th>
      <td>94264</td>
      <td>9821</td>
      <td>84444</td>
      <td>56.16</td>
      <td>1.3</td>
      <td>3.28</td>
      <td>1.22</td>
    </tr>
    <tr>
      <th>2018년12월</th>
      <td>79698</td>
      <td>9093</td>
      <td>70605</td>
      <td>64.92</td>
      <td>1.02</td>
      <td>3.34</td>
      <td>0.93</td>
    </tr>
    <tr>
      <th>2019년03월</th>
      <td>78193</td>
      <td>9093</td>
      <td>69100</td>
      <td>73.9</td>
      <td>1.07</td>
      <td>2.8</td>
      <td>0.99</td>
    </tr>
    <tr>
      <th>2019년06월</th>
      <td>61937</td>
      <td>9093</td>
      <td>52845</td>
      <td>90.49</td>
      <td>0.84</td>
      <td>2.96</td>
      <td>0.74</td>
    </tr>
    <tr>
      <th>2019년09월</th>
      <td>61002</td>
      <td>9093</td>
      <td>51909</td>
      <td>97.47</td>
      <td>0.76</td>
      <td>2.49</td>
      <td>0.66</td>
    </tr>
    <tr>
      <th>2019년12월</th>
      <td>61382</td>
      <td>9093</td>
      <td>52289</td>
      <td>90.18</td>
      <td>0.74</td>
      <td>2.93</td>
      <td>0.64</td>
    </tr>
    <tr>
      <th>2020년03월</th>
      <td>70293</td>
      <td>9093</td>
      <td>61200</td>
      <td>78.19</td>
      <td>0.92</td>
      <td>3.37</td>
      <td>0.82</td>
    </tr>
    <tr>
      <th>2020년06월</th>
      <td>61802</td>
      <td>9093</td>
      <td>52709</td>
      <td>93.2</td>
      <td>0.8</td>
      <td>2.47</td>
      <td>0.72</td>
    </tr>
    <tr>
      <th>2020년09월</th>
      <td>65136</td>
      <td>9093</td>
      <td>56043</td>
      <td>95.96</td>
      <td>0.77</td>
      <td>2.26</td>
      <td>0.69</td>
    </tr>
    <tr>
      <th>2020년12월</th>
      <td>65360</td>
      <td>9093</td>
      <td>56266</td>
      <td>122.06</td>
      <td>0.6</td>
      <td>2.31</td>
      <td>0.52</td>
    </tr>
    <tr>
      <th>2021년03월</th>
      <td>66314</td>
      <td>9093</td>
      <td>57222</td>
      <td>120.03</td>
      <td>0.71</td>
      <td>2.38</td>
      <td>0.63</td>
    </tr>
    <tr>
      <th>2021년06월</th>
      <td>68474</td>
      <td>9093</td>
      <td>59380</td>
      <td>123.58</td>
      <td>0.71</td>
      <td>2.71</td>
      <td>0.62</td>
    </tr>
    <tr>
      <th>2021년09월</th>
      <td>77971</td>
      <td>9093</td>
      <td>68877</td>
      <td>115.28</td>
      <td>0.71</td>
      <td>2.04</td>
      <td>0.64</td>
    </tr>
    <tr>
      <th>2021년12월</th>
      <td>47087</td>
      <td>0</td>
      <td>47088</td>
      <td>177.95</td>
      <td>0.37</td>
      <td>0</td>
      <td>0.38</td>
    </tr>
    <tr>
      <th>2022년03월</th>
      <td>39699</td>
      <td>0</td>
      <td>39697</td>
      <td>198.14</td>
      <td>0.4</td>
      <td>0</td>
      <td>0.42</td>
    </tr>
    <tr>
      <th>2022년06월</th>
      <td>44135</td>
      <td>0</td>
      <td>44135</td>
      <td>193.74</td>
      <td>0.41</td>
      <td>0</td>
      <td>0.43</td>
    </tr>
    <tr>
      <th>2022년09월</th>
      <td>50463</td>
      <td>0</td>
      <td>50463</td>
      <td>184.31</td>
      <td>0.5</td>
      <td>0</td>
      <td>0.52</td>
    </tr>
  </tbody>
</table>
</div>




```python
## 고정이하여신-기업/대기업/중소기업
plt.figure(figsize=(20,8))
plt.plot(fis2[['기업여신:고정이하여신','기업여신_대기업:고정이하여신','기업여신_중소기업:고정이하여신']],lw=3)
plt.grid(True)
plt.legend(fis2.columns[:3],fontsize=20)
plt.show()
```


    
![png](output_13_0.png)
    



```python
## 대손충당금적립비율-고정이하여신대비
plt.figure(figsize=(20,8))
plt.plot(fis2['대손충당금적립비율(고정이하여신대비)'],lw=3,label='대손충당금적립비율(고정이하여신대비)')
plt.grid(True)
plt.legend(loc='upper left',fontsize=20)
plt.show()
```


    
![png](output_14_0.png)
    



```python
##기업대출_연체율 /대기업대출_연체율 /중소기업대출_연체율
plt.figure(figsize=(25,8))
plt.plot(fis2[['기업대출_연체율','기업대출_대기업대출_연체율','기업대출_중소기업대출_연체율']],lw=3)

#labels=()'기업대출_연체율','기업대출_대기업대출_연체율','기업대출_중소기업대출_연체율']
#plt.legend(fis2.columns[7:],fontsize=20)
plt.legend(fis2[['기업대출_연체율','기업대출_대기업대출_연체율','기업대출_중소기업대출_연체율']],loc='upper left',fontsize=15)
plt.show()
```


    
![png](output_15_0.png)
    



```python
NSFR.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>총 고유동성자산</th>
      <th>순현금유출액</th>
      <th>순안정자금조달비율</th>
      <th>유동성커버리지비율</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>2.300000e+01</td>
      <td>2.300000e+01</td>
      <td>23.000000</td>
      <td>23.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2.282508e+06</td>
      <td>2.052084e+06</td>
      <td>88.521739</td>
      <td>111.086957</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3.101680e+05</td>
      <td>2.863366e+05</td>
      <td>41.631358</td>
      <td>6.748152</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.899934e+06</td>
      <td>1.541845e+06</td>
      <td>0.000000</td>
      <td>102.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2.094146e+06</td>
      <td>1.860431e+06</td>
      <td>103.000000</td>
      <td>105.500000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2.170533e+06</td>
      <td>2.079978e+06</td>
      <td>106.000000</td>
      <td>110.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2.314120e+06</td>
      <td>2.223814e+06</td>
      <td>109.500000</td>
      <td>115.500000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>3.052585e+06</td>
      <td>2.609542e+06</td>
      <td>112.000000</td>
      <td>126.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
fis2.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>기업여신:고정이하여신</th>
      <th>기업여신_대기업:고정이하여신</th>
      <th>기업여신_중소기업:고정이하여신</th>
      <th>대손충당금적립비율(고정이하여신대비)</th>
      <th>기업대출_연체율</th>
      <th>기업대출_대기업대출_연체율</th>
      <th>기업대출_중소기업대출_연체율</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>23</td>
      <td>23</td>
      <td>23</td>
      <td>23.00</td>
      <td>23.00</td>
      <td>23.0</td>
      <td>23.00</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>23</td>
      <td>6</td>
      <td>23</td>
      <td>23.00</td>
      <td>21.00</td>
      <td>19.0</td>
      <td>20.00</td>
    </tr>
    <tr>
      <th>top</th>
      <td>115811</td>
      <td>9093</td>
      <td>105976</td>
      <td>45.84</td>
      <td>0.71</td>
      <td>0.0</td>
      <td>0.64</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>1</td>
      <td>12</td>
      <td>1</td>
      <td>1.00</td>
      <td>3.00</td>
      <td>4.0</td>
      <td>2.00</td>
    </tr>
  </tbody>
</table>
</div>




```python
#### 업종별 대출금
d = pd.read_excel('업종별대출.xls')
d
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>복수 통계표 조회결과_201703~202209</th>
      <th>Unnamed: 1</th>
      <th>Unnamed: 2</th>
      <th>Unnamed: 3</th>
      <th>Unnamed: 4</th>
      <th>Unnamed: 5</th>
      <th>Unnamed: 6</th>
      <th>Unnamed: 7</th>
      <th>Unnamed: 8</th>
      <th>Unnamed: 9</th>
      <th>...</th>
      <th>Unnamed: 20</th>
      <th>Unnamed: 21</th>
      <th>Unnamed: 22</th>
      <th>Unnamed: 23</th>
      <th>Unnamed: 24</th>
      <th>Unnamed: 25</th>
      <th>Unnamed: 26</th>
      <th>Unnamed: 27</th>
      <th>Unnamed: 28</th>
      <th>Unnamed: 29</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>회사명</td>
      <td>회사코드</td>
      <td>보고서명</td>
      <td>보고서코드</td>
      <td>항목</td>
      <td>factor_id</td>
      <td>단위</td>
      <td>2017년03월</td>
      <td>2017년06월</td>
      <td>2017년09월</td>
      <td>...</td>
      <td>2020년06월</td>
      <td>2020년09월</td>
      <td>2020년12월</td>
      <td>2021년03월</td>
      <td>2021년06월</td>
      <td>2021년09월</td>
      <td>2021년12월</td>
      <td>2022년03월</td>
      <td>2022년06월</td>
      <td>2022년09월</td>
    </tr>
    <tr>
      <th>1</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유형별 대출채권(업종별 기업대출금)</td>
      <td>SDSA044V</td>
      <td>기업대출금 계</td>
      <td>F000002097</td>
      <td>백만원</td>
      <td>6944640</td>
      <td>6947505</td>
      <td>6911679</td>
      <td>...</td>
      <td>7658068</td>
      <td>7930619</td>
      <td>8063799</td>
      <td>8086997</td>
      <td>7986953</td>
      <td>8361782</td>
      <td>8362648</td>
      <td>8594789</td>
      <td>8761277</td>
      <td>8946404</td>
    </tr>
    <tr>
      <th>2</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유형별 대출채권(업종별 기업대출금)</td>
      <td>SDSA044V</td>
      <td>농림어업</td>
      <td>F000002098</td>
      <td>백만원</td>
      <td>24219</td>
      <td>27064</td>
      <td>28569</td>
      <td>...</td>
      <td>27815</td>
      <td>26399</td>
      <td>27768</td>
      <td>29034</td>
      <td>29879</td>
      <td>30652</td>
      <td>33451</td>
      <td>34141</td>
      <td>32769</td>
      <td>37729</td>
    </tr>
    <tr>
      <th>3</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유형별 대출채권(업종별 기업대출금)</td>
      <td>SDSA044V</td>
      <td>제조업</td>
      <td>F000002099</td>
      <td>백만원</td>
      <td>905014</td>
      <td>868227</td>
      <td>868299</td>
      <td>...</td>
      <td>771114</td>
      <td>771261</td>
      <td>747465</td>
      <td>739585</td>
      <td>713667</td>
      <td>716243</td>
      <td>718535</td>
      <td>729760</td>
      <td>736735</td>
      <td>772781</td>
    </tr>
    <tr>
      <th>4</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유형별 대출채권(업종별 기업대출금)</td>
      <td>SDSA044V</td>
      <td>건설업</td>
      <td>F000002100</td>
      <td>백만원</td>
      <td>526076</td>
      <td>526721</td>
      <td>523254</td>
      <td>...</td>
      <td>590224</td>
      <td>613208</td>
      <td>522797</td>
      <td>490737</td>
      <td>462238</td>
      <td>459929</td>
      <td>414836</td>
      <td>439046</td>
      <td>418888</td>
      <td>455827</td>
    </tr>
    <tr>
      <th>5</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유형별 대출채권(업종별 기업대출금)</td>
      <td>SDSA044V</td>
      <td>도·소매업</td>
      <td>F000002101</td>
      <td>백만원</td>
      <td>966619</td>
      <td>959830</td>
      <td>935595</td>
      <td>...</td>
      <td>870618</td>
      <td>878179</td>
      <td>860051</td>
      <td>858389</td>
      <td>862475</td>
      <td>863014</td>
      <td>866459</td>
      <td>883214</td>
      <td>884042</td>
      <td>895471</td>
    </tr>
    <tr>
      <th>6</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유형별 대출채권(업종별 기업대출금)</td>
      <td>SDSA044V</td>
      <td>운수업</td>
      <td>F000002102</td>
      <td>백만원</td>
      <td>84106</td>
      <td>94753</td>
      <td>93742</td>
      <td>...</td>
      <td>92612</td>
      <td>94697</td>
      <td>94127</td>
      <td>94774</td>
      <td>88561</td>
      <td>92367</td>
      <td>92393</td>
      <td>102681</td>
      <td>107324</td>
      <td>110832</td>
    </tr>
    <tr>
      <th>7</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유형별 대출채권(업종별 기업대출금)</td>
      <td>SDSA044V</td>
      <td>숙박·음식업</td>
      <td>F000002103</td>
      <td>백만원</td>
      <td>433528</td>
      <td>419068</td>
      <td>410872</td>
      <td>...</td>
      <td>380958</td>
      <td>383504</td>
      <td>391615</td>
      <td>397613</td>
      <td>398011</td>
      <td>397113</td>
      <td>418069</td>
      <td>421383</td>
      <td>426448</td>
      <td>447199</td>
    </tr>
    <tr>
      <th>8</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유형별 대출채권(업종별 기업대출금)</td>
      <td>SDSA044V</td>
      <td>통신업</td>
      <td>F000002104</td>
      <td>백만원</td>
      <td>995</td>
      <td>1194</td>
      <td>1002</td>
      <td>...</td>
      <td>715</td>
      <td>855</td>
      <td>800</td>
      <td>753</td>
      <td>980</td>
      <td>1397</td>
      <td>1345</td>
      <td>1424</td>
      <td>1448</td>
      <td>1396</td>
    </tr>
    <tr>
      <th>9</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유형별 대출채권(업종별 기업대출금)</td>
      <td>SDSA044V</td>
      <td>부동산및임대업</td>
      <td>F000002105</td>
      <td>백만원</td>
      <td>2635121</td>
      <td>2737785</td>
      <td>2762974</td>
      <td>...</td>
      <td>3262629</td>
      <td>3375053</td>
      <td>3540898</td>
      <td>3511221</td>
      <td>3446181</td>
      <td>3742424</td>
      <td>3718371</td>
      <td>3853439</td>
      <td>3963849</td>
      <td>3998301</td>
    </tr>
    <tr>
      <th>10</th>
      <td>전북은행</td>
      <td>0010022</td>
      <td>유형별 대출채권(업종별 기업대출금)</td>
      <td>SDSA044V</td>
      <td>기타</td>
      <td>F000002106</td>
      <td>백만원</td>
      <td>1368962</td>
      <td>1312863</td>
      <td>1287372</td>
      <td>...</td>
      <td>1661383</td>
      <td>1787463</td>
      <td>1878278</td>
      <td>1964891</td>
      <td>1984961</td>
      <td>2058643</td>
      <td>2099189</td>
      <td>2129701</td>
      <td>2189774</td>
      <td>2226868</td>
    </tr>
  </tbody>
</table>
<p>11 rows × 30 columns</p>
</div>



## 기업대출금 


```python
## 기업대출금 -건설업/부동산및임대업
a = pd.concat([d.loc[0],d.loc[1],d.loc[4],d.loc[9]],axis=1).reset_index(drop=True)
a= a.rename(columns={ 1:'총 기업대출금',4:"기업대출금_건설업",9:'기업대출금_부동산및임대업'}).loc[7:]
a = a.set_index([0])
a.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>총 기업대출금</th>
      <th>기업대출금_건설업</th>
      <th>기업대출금_부동산및임대업</th>
    </tr>
    <tr>
      <th>0</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017년03월</th>
      <td>6944640</td>
      <td>526076</td>
      <td>2635121</td>
    </tr>
    <tr>
      <th>2017년06월</th>
      <td>6947505</td>
      <td>526721</td>
      <td>2737785</td>
    </tr>
    <tr>
      <th>2017년09월</th>
      <td>6911679</td>
      <td>523254</td>
      <td>2762974</td>
    </tr>
    <tr>
      <th>2017년12월</th>
      <td>6952426</td>
      <td>484247</td>
      <td>2858811</td>
    </tr>
    <tr>
      <th>2018년03월</th>
      <td>7057963</td>
      <td>485172</td>
      <td>3013340</td>
    </tr>
  </tbody>
</table>
</div>




```python
## 표저장
#a.to_csv('jb-기업대출금.csv')
```


```python
## 기업대출금 -건설업/부동산및임대업 -그래프
plt.figure(figsize=(27,5))
plt.plot(a,lw=3)
plt.grid(True)
plt.legend(a,fontsize=14)
plt.show()
```


    
![png](output_22_0.png)
    



```python
# 업종별 대출(부동산, 건설업) 증감액이 전체 기업대출에서 차지하는 비율 
a = a.astype(int)
건설업 = a['기업대출금_건설업']/a['총 기업대출금']
부동산 = a['기업대출금_부동산및임대업']/a['총 기업대출금']
k = pd.concat([건설업,부동산],axis=1)
k=k.rename(columns={ 0:'대출금비율_건설업',1:'대출금비율_부동산'})
k.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>대출금비율_건설업</th>
      <th>대출금비율_부동산</th>
    </tr>
    <tr>
      <th>0</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017년03월</th>
      <td>0.075753</td>
      <td>0.379447</td>
    </tr>
    <tr>
      <th>2017년06월</th>
      <td>0.075814</td>
      <td>0.394067</td>
    </tr>
    <tr>
      <th>2017년09월</th>
      <td>0.075706</td>
      <td>0.399754</td>
    </tr>
    <tr>
      <th>2017년12월</th>
      <td>0.069652</td>
      <td>0.411196</td>
    </tr>
    <tr>
      <th>2018년03월</th>
      <td>0.068741</td>
      <td>0.426942</td>
    </tr>
  </tbody>
</table>
</div>




```python
### 총대출금 대비 -부동산&건설업 퍼센트로 표현
총대출금대비_부동산_건설업_퍼센트 = k*100
총대출금대비_부동산_건설업_퍼센트
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>대출금비율_건설업</th>
      <th>대출금비율_부동산</th>
    </tr>
    <tr>
      <th>0</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017년03월</th>
      <td>7.575281</td>
      <td>37.944674</td>
    </tr>
    <tr>
      <th>2017년06월</th>
      <td>7.581441</td>
      <td>39.406737</td>
    </tr>
    <tr>
      <th>2017년09월</th>
      <td>7.570577</td>
      <td>39.975439</td>
    </tr>
    <tr>
      <th>2017년12월</th>
      <td>6.965151</td>
      <td>41.119618</td>
    </tr>
    <tr>
      <th>2018년03월</th>
      <td>6.874108</td>
      <td>42.694188</td>
    </tr>
    <tr>
      <th>2018년06월</th>
      <td>6.461399</td>
      <td>44.218631</td>
    </tr>
    <tr>
      <th>2018년09월</th>
      <td>6.258585</td>
      <td>44.606697</td>
    </tr>
    <tr>
      <th>2018년12월</th>
      <td>5.813318</td>
      <td>45.351231</td>
    </tr>
    <tr>
      <th>2019년03월</th>
      <td>6.649921</td>
      <td>44.531931</td>
    </tr>
    <tr>
      <th>2019년06월</th>
      <td>7.024914</td>
      <td>44.712582</td>
    </tr>
    <tr>
      <th>2019년09월</th>
      <td>7.167742</td>
      <td>44.790903</td>
    </tr>
    <tr>
      <th>2019년12월</th>
      <td>7.106501</td>
      <td>43.540128</td>
    </tr>
    <tr>
      <th>2020년03월</th>
      <td>7.703077</td>
      <td>41.894930</td>
    </tr>
    <tr>
      <th>2020년06월</th>
      <td>7.707218</td>
      <td>42.603813</td>
    </tr>
    <tr>
      <th>2020년09월</th>
      <td>7.732158</td>
      <td>42.557246</td>
    </tr>
    <tr>
      <th>2020년12월</th>
      <td>6.483259</td>
      <td>43.911040</td>
    </tr>
    <tr>
      <th>2021년03월</th>
      <td>6.068223</td>
      <td>43.418107</td>
    </tr>
    <tr>
      <th>2021년06월</th>
      <td>5.787414</td>
      <td>43.147631</td>
    </tr>
    <tr>
      <th>2021년09월</th>
      <td>5.500371</td>
      <td>44.756297</td>
    </tr>
    <tr>
      <th>2021년12월</th>
      <td>4.960582</td>
      <td>44.464038</td>
    </tr>
    <tr>
      <th>2022년03월</th>
      <td>5.108281</td>
      <td>44.834597</td>
    </tr>
    <tr>
      <th>2022년06월</th>
      <td>4.781130</td>
      <td>45.242822</td>
    </tr>
    <tr>
      <th>2022년09월</th>
      <td>5.095086</td>
      <td>44.691711</td>
    </tr>
  </tbody>
</table>
</div>




```python
## 기업대출금 중 건설업 과 부동산및임대업 비율 --비교 그래프
plt.figure(figsize=(27,5))
plt.plot(k,lw=3)
plt.grid(True)
plt.legend(k,fontsize=14)
plt.show()
```


    
![png](output_25_0.png)
    



```python
## 총대출금에서 (건설업+부동산) 대출금이 차지하는 비율 그래프
b = pd.concat([ a['총 기업대출금'],a['기업대출금_건설업']+a['기업대출금_부동산및임대업']],axis=1)
b = b.rename(columns={ 0:'기업대출금_건설업+부동산'})
b.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>총 기업대출금</th>
      <th>기업대출금_건설업+부동산</th>
    </tr>
    <tr>
      <th>0</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017년03월</th>
      <td>6944640</td>
      <td>3161197</td>
    </tr>
    <tr>
      <th>2017년06월</th>
      <td>6947505</td>
      <td>3264506</td>
    </tr>
    <tr>
      <th>2017년09월</th>
      <td>6911679</td>
      <td>3286228</td>
    </tr>
    <tr>
      <th>2017년12월</th>
      <td>6952426</td>
      <td>3343058</td>
    </tr>
    <tr>
      <th>2018년03월</th>
      <td>7057963</td>
      <td>3498512</td>
    </tr>
  </tbody>
</table>
</div>




```python
b.plot.bar(rot=0,figsize=(25,8))
```




    <AxesSubplot:xlabel='0'>




    
![png](output_27_1.png)
    


## 모든 변수 상관관계


```python
all = pd.concat([NSFR,
fis2['기업여신:고정이하여신'],
fis2['대손충당금적립비율(고정이하여신대비)'],
fis2['기업대출_연체율'],
a['총 기업대출금']],axis=1)
all = all.astype(int)
all
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>총 고유동성자산</th>
      <th>순현금유출액</th>
      <th>순안정자금조달비율</th>
      <th>유동성커버리지비율</th>
      <th>기업여신:고정이하여신</th>
      <th>대손충당금적립비율(고정이하여신대비)</th>
      <th>기업대출_연체율</th>
      <th>총 기업대출금</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017년03월</th>
      <td>1899934</td>
      <td>1541845</td>
      <td>0</td>
      <td>123</td>
      <td>115811</td>
      <td>45</td>
      <td>1</td>
      <td>6944640</td>
    </tr>
    <tr>
      <th>2017년06월</th>
      <td>2014544</td>
      <td>1589359</td>
      <td>0</td>
      <td>126</td>
      <td>110552</td>
      <td>46</td>
      <td>1</td>
      <td>6947505</td>
    </tr>
    <tr>
      <th>2017년09월</th>
      <td>2146704</td>
      <td>1953446</td>
      <td>0</td>
      <td>109</td>
      <td>93609</td>
      <td>47</td>
      <td>1</td>
      <td>6911679</td>
    </tr>
    <tr>
      <th>2017년12월</th>
      <td>2221235</td>
      <td>2139108</td>
      <td>0</td>
      <td>103</td>
      <td>95324</td>
      <td>44</td>
      <td>1</td>
      <td>6952426</td>
    </tr>
    <tr>
      <th>2018년03월</th>
      <td>2099805</td>
      <td>1932949</td>
      <td>111</td>
      <td>108</td>
      <td>91132</td>
      <td>59</td>
      <td>1</td>
      <td>7057963</td>
    </tr>
    <tr>
      <th>2018년06월</th>
      <td>2210747</td>
      <td>2141616</td>
      <td>112</td>
      <td>103</td>
      <td>95088</td>
      <td>55</td>
      <td>1</td>
      <td>6993222</td>
    </tr>
    <tr>
      <th>2018년09월</th>
      <td>2152376</td>
      <td>1855382</td>
      <td>110</td>
      <td>116</td>
      <td>94264</td>
      <td>56</td>
      <td>1</td>
      <td>6989807</td>
    </tr>
    <tr>
      <th>2018년12월</th>
      <td>2066364</td>
      <td>1865480</td>
      <td>110</td>
      <td>110</td>
      <td>79698</td>
      <td>64</td>
      <td>1</td>
      <td>6943161</td>
    </tr>
    <tr>
      <th>2019년03월</th>
      <td>1945224</td>
      <td>1746519</td>
      <td>111</td>
      <td>111</td>
      <td>78193</td>
      <td>73</td>
      <td>1</td>
      <td>7055407</td>
    </tr>
    <tr>
      <th>2019년06월</th>
      <td>2122067</td>
      <td>1963055</td>
      <td>112</td>
      <td>108</td>
      <td>61937</td>
      <td>90</td>
      <td>0</td>
      <td>7084044</td>
    </tr>
    <tr>
      <th>2019년09월</th>
      <td>2070408</td>
      <td>1789174</td>
      <td>106</td>
      <td>115</td>
      <td>61002</td>
      <td>97</td>
      <td>0</td>
      <td>7107441</td>
    </tr>
    <tr>
      <th>2019년12월</th>
      <td>2141579</td>
      <td>1899757</td>
      <td>108</td>
      <td>112</td>
      <td>61382</td>
      <td>90</td>
      <td>0</td>
      <td>7105156</td>
    </tr>
    <tr>
      <th>2020년03월</th>
      <td>2088486</td>
      <td>1789109</td>
      <td>108</td>
      <td>116</td>
      <td>70293</td>
      <td>78</td>
      <td>0</td>
      <td>7248259</td>
    </tr>
    <tr>
      <th>2020년06월</th>
      <td>2170533</td>
      <td>2081465</td>
      <td>103</td>
      <td>104</td>
      <td>61802</td>
      <td>93</td>
      <td>0</td>
      <td>7658068</td>
    </tr>
    <tr>
      <th>2020년09월</th>
      <td>2336699</td>
      <td>2214942</td>
      <td>105</td>
      <td>105</td>
      <td>65136</td>
      <td>95</td>
      <td>0</td>
      <td>7930619</td>
    </tr>
    <tr>
      <th>2020년12월</th>
      <td>2291540</td>
      <td>2237740</td>
      <td>105</td>
      <td>102</td>
      <td>65360</td>
      <td>122</td>
      <td>0</td>
      <td>8063799</td>
    </tr>
    <tr>
      <th>2021년03월</th>
      <td>2269091</td>
      <td>2079978</td>
      <td>106</td>
      <td>109</td>
      <td>66314</td>
      <td>120</td>
      <td>0</td>
      <td>8086997</td>
    </tr>
    <tr>
      <th>2021년06월</th>
      <td>2266289</td>
      <td>2145982</td>
      <td>109</td>
      <td>105</td>
      <td>68474</td>
      <td>123</td>
      <td>0</td>
      <td>7986953</td>
    </tr>
    <tr>
      <th>2021년09월</th>
      <td>2488655</td>
      <td>2347067</td>
      <td>104</td>
      <td>106</td>
      <td>77971</td>
      <td>115</td>
      <td>0</td>
      <td>8361782</td>
    </tr>
    <tr>
      <th>2021년12월</th>
      <td>2722469</td>
      <td>2442978</td>
      <td>106</td>
      <td>111</td>
      <td>47087</td>
      <td>177</td>
      <td>0</td>
      <td>8362648</td>
    </tr>
    <tr>
      <th>2022년03월</th>
      <td>2958848</td>
      <td>2609542</td>
      <td>105</td>
      <td>113</td>
      <td>39699</td>
      <td>198</td>
      <td>0</td>
      <td>8594789</td>
    </tr>
    <tr>
      <th>2022년06월</th>
      <td>2761502</td>
      <td>2232686</td>
      <td>103</td>
      <td>123</td>
      <td>44135</td>
      <td>193</td>
      <td>0</td>
      <td>8761277</td>
    </tr>
    <tr>
      <th>2022년09월</th>
      <td>3052585</td>
      <td>2598757</td>
      <td>102</td>
      <td>117</td>
      <td>50463</td>
      <td>184</td>
      <td>0</td>
      <td>8946404</td>
    </tr>
  </tbody>
</table>
</div>




```python
## 상관계수
all.corr()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>총 고유동성자산</th>
      <th>순현금유출액</th>
      <th>순안정자금조달비율</th>
      <th>유동성커버리지비율</th>
      <th>기업여신:고정이하여신</th>
      <th>대손충당금적립비율(고정이하여신대비)</th>
      <th>기업대출_연체율</th>
      <th>총 기업대출금</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>총 고유동성자산</th>
      <td>1.000000</td>
      <td>0.909350</td>
      <td>0.276039</td>
      <td>0.055440</td>
      <td>-0.697264</td>
      <td>0.894388</td>
      <td>-0.524402</td>
      <td>0.893941</td>
    </tr>
    <tr>
      <th>순현금유출액</th>
      <td>0.909350</td>
      <td>1.000000</td>
      <td>0.365488</td>
      <td>-0.361234</td>
      <td>-0.679443</td>
      <td>0.789812</td>
      <td>-0.541775</td>
      <td>0.837230</td>
    </tr>
    <tr>
      <th>순안정자금조달비율</th>
      <td>0.276039</td>
      <td>0.365488</td>
      <td>1.000000</td>
      <td>-0.299980</td>
      <td>-0.650651</td>
      <td>0.461081</td>
      <td>-0.531017</td>
      <td>0.377691</td>
    </tr>
    <tr>
      <th>유동성커버리지비율</th>
      <td>0.055440</td>
      <td>-0.361234</td>
      <td>-0.299980</td>
      <td>1.000000</td>
      <td>0.113046</td>
      <td>0.099794</td>
      <td>0.124420</td>
      <td>0.006972</td>
    </tr>
    <tr>
      <th>기업여신:고정이하여신</th>
      <td>-0.697264</td>
      <td>-0.679443</td>
      <td>-0.650651</td>
      <td>0.113046</td>
      <td>1.000000</td>
      <td>-0.873479</td>
      <td>0.841275</td>
      <td>-0.739254</td>
    </tr>
    <tr>
      <th>대손충당금적립비율(고정이하여신대비)</th>
      <td>0.894388</td>
      <td>0.789812</td>
      <td>0.461081</td>
      <td>0.099794</td>
      <td>-0.873479</td>
      <td>1.000000</td>
      <td>-0.735639</td>
      <td>0.931777</td>
    </tr>
    <tr>
      <th>기업대출_연체율</th>
      <td>-0.524402</td>
      <td>-0.541775</td>
      <td>-0.531017</td>
      <td>0.124420</td>
      <td>0.841275</td>
      <td>-0.735639</td>
      <td>1.000000</td>
      <td>-0.706066</td>
    </tr>
    <tr>
      <th>총 기업대출금</th>
      <td>0.893941</td>
      <td>0.837230</td>
      <td>0.377691</td>
      <td>0.006972</td>
      <td>-0.739254</td>
      <td>0.931777</td>
      <td>-0.706066</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.ioff()
std_var = '유동성커버리지비율'

for col in all.columns:
    if '순안정자금조달비율' in col:
        std_vector = all.dropna()[std_var]
        oth_vector = all.dropna()[col]
    elif col == std_var:
        continue
    else:
        std_vector = all[std_var]
        oth_vector = all[col]
        
    print(f'{std_var} & {col} 상관계수 : {np.corrcoef(std_vector, oth_vector)[0, 1]}')
    plt.figure(figsize=(26, 6))
    sns.lineplot(data=all[std_var], color='g')
    sns.lineplot(data=all[col], color='r', ax=plt.twinx())
    plt.show()
    print()
    print('=' * 100)
    print()
```

    유동성커버리지비율 & 총 고유동성자산 상관계수 : 0.05544040105164714



    
![png](output_31_1.png)
    


    
    ====================================================================================================
    
    유동성커버리지비율 & 순현금유출액 상관계수 : -0.3612336607497513



    
![png](output_31_3.png)
    


    
    ====================================================================================================
    
    유동성커버리지비율 & 순안정자금조달비율 상관계수 : -0.2999796742718252



    
![png](output_31_5.png)
    


    
    ====================================================================================================
    
    유동성커버리지비율 & 기업여신:고정이하여신 상관계수 : 0.11304595976051561



    
![png](output_31_7.png)
    


    
    ====================================================================================================
    
    유동성커버리지비율 & 대손충당금적립비율(고정이하여신대비) 상관계수 : 0.09979382349155733



    
![png](output_31_9.png)
    


    
    ====================================================================================================
    
    유동성커버리지비율 & 기업대출_연체율 상관계수 : 0.12442008744147824



    
![png](output_31_11.png)
    


    
    ====================================================================================================
    
    유동성커버리지비율 & 총 기업대출금 상관계수 : 0.006972370462669297



    
![png](output_31_13.png)
    


    
    ====================================================================================================
    



```python
all.shape
```




    (23, 8)


