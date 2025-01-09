Tags: [[Pandas]] [[Datasets]] [[Programming]] [[Python]] #Pandas #Python
### Datasets
Textual datasets can be stored in many different formats including
- CSV
- JSON
- SQL
- Many Others
  **By Far the most commonly used is CSV**
  Comman-Separated Values



```python
import pandas as pd
```

### Reading a csv file with pandas


```python
pd.read_csv("C:\\Users\\hacks\\Documents\\MyNotebooks\\data\\states.csv")
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
      <th>State</th>
      <th>Abbrev</th>
      <th>Code</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alabama</td>
      <td>Ala.</td>
      <td>AL</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Alaska</td>
      <td>Alaska</td>
      <td>AK</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Arizona</td>
      <td>Ariz.</td>
      <td>AZ</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Arkansas</td>
      <td>Ark.</td>
      <td>AR</td>
    </tr>
    <tr>
      <th>4</th>
      <td>California</td>
      <td>Calif.</td>
      <td>CA</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Colorado</td>
      <td>Colo.</td>
      <td>CO</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Connecticut</td>
      <td>Conn.</td>
      <td>CT</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Delaware</td>
      <td>Del.</td>
      <td>DE</td>
    </tr>
    <tr>
      <th>8</th>
      <td>District of Columbia</td>
      <td>D.C.</td>
      <td>DC</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Florida</td>
      <td>Fla.</td>
      <td>FL</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Georgia</td>
      <td>Ga.</td>
      <td>GA</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Hawaii</td>
      <td>Hawaii</td>
      <td>HI</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Idaho</td>
      <td>Idaho</td>
      <td>ID</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Illinois</td>
      <td>Ill.</td>
      <td>IL</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Indiana</td>
      <td>Ind.</td>
      <td>IN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Iowa</td>
      <td>Iowa</td>
      <td>IA</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Kansas</td>
      <td>Kans.</td>
      <td>KS</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Kentucky</td>
      <td>Ky.</td>
      <td>KY</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Louisiana</td>
      <td>La.</td>
      <td>LA</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Maine</td>
      <td>Maine</td>
      <td>ME</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Maryland</td>
      <td>Md.</td>
      <td>MD</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Massachusetts</td>
      <td>Mass.</td>
      <td>MA</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Michigan</td>
      <td>Mich.</td>
      <td>MI</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Minnesota</td>
      <td>Minn.</td>
      <td>MN</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Mississippi</td>
      <td>Miss.</td>
      <td>MS</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Missouri</td>
      <td>Mo.</td>
      <td>MO</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Montana</td>
      <td>Mont.</td>
      <td>MT</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Nebraska</td>
      <td>Nebr.</td>
      <td>NE</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Nevada</td>
      <td>Nev.</td>
      <td>NV</td>
    </tr>
    <tr>
      <th>29</th>
      <td>New Hampshire</td>
      <td>N.H.</td>
      <td>NH</td>
    </tr>
    <tr>
      <th>30</th>
      <td>New Jersey</td>
      <td>N.J.</td>
      <td>NJ</td>
    </tr>
    <tr>
      <th>31</th>
      <td>New Mexico</td>
      <td>N.M.</td>
      <td>NM</td>
    </tr>
    <tr>
      <th>32</th>
      <td>New York</td>
      <td>N.Y.</td>
      <td>NY</td>
    </tr>
    <tr>
      <th>33</th>
      <td>North Carolina</td>
      <td>N.C.</td>
      <td>NC</td>
    </tr>
    <tr>
      <th>34</th>
      <td>North Dakota</td>
      <td>N.D.</td>
      <td>ND</td>
    </tr>
    <tr>
      <th>35</th>
      <td>Ohio</td>
      <td>Ohio</td>
      <td>OH</td>
    </tr>
    <tr>
      <th>36</th>
      <td>Oklahoma</td>
      <td>Okla.</td>
      <td>OK</td>
    </tr>
    <tr>
      <th>37</th>
      <td>Oregon</td>
      <td>Ore.</td>
      <td>OR</td>
    </tr>
    <tr>
      <th>38</th>
      <td>Pennsylvania</td>
      <td>Pa.</td>
      <td>PA</td>
    </tr>
    <tr>
      <th>39</th>
      <td>Rhode Island</td>
      <td>R.I.</td>
      <td>RI</td>
    </tr>
    <tr>
      <th>40</th>
      <td>South Carolina</td>
      <td>S.C.</td>
      <td>SC</td>
    </tr>
    <tr>
      <th>41</th>
      <td>South Dakota</td>
      <td>S.D.</td>
      <td>SD</td>
    </tr>
    <tr>
      <th>42</th>
      <td>Tennessee</td>
      <td>Tenn.</td>
      <td>TN</td>
    </tr>
    <tr>
      <th>43</th>
      <td>Texas</td>
      <td>Tex.</td>
      <td>TX</td>
    </tr>
    <tr>
      <th>44</th>
      <td>Utah</td>
      <td>Utah</td>
      <td>UT</td>
    </tr>
    <tr>
      <th>45</th>
      <td>Vermont</td>
      <td>Vt.</td>
      <td>VT</td>
    </tr>
    <tr>
      <th>46</th>
      <td>Virginia</td>
      <td>Va.</td>
      <td>VA</td>
    </tr>
    <tr>
      <th>47</th>
      <td>Washington</td>
      <td>Wash.</td>
      <td>WA</td>
    </tr>
    <tr>
      <th>48</th>
      <td>West Virginia</td>
      <td>W.Va.</td>
      <td>WV</td>
    </tr>
    <tr>
      <th>49</th>
      <td>Wisconsin</td>
      <td>Wis.</td>
      <td>WI</td>
    </tr>
    <tr>
      <th>50</th>
      <td>Wyoming</td>
      <td>Wyo.</td>
      <td>WY</td>
    </tr>
  </tbody>
</table>
</div>



### Setting it to a variable


```python
houses = pd.read_csv("C:\\Users\\hacks\\Documents\\MyNotebooks\\data\\kc_house_data.csv")
```


```python
houses
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
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>...</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>20141013T000000</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1180</td>
      <td>0</td>
      <td>1955</td>
      <td>0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>20141209T000000</td>
      <td>538000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>2170</td>
      <td>400</td>
      <td>1951</td>
      <td>1991</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5631500400</td>
      <td>20150225T000000</td>
      <td>180000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>770</td>
      <td>10000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>6</td>
      <td>770</td>
      <td>0</td>
      <td>1933</td>
      <td>0</td>
      <td>98028</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720</td>
      <td>8062</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2487200875</td>
      <td>20141209T000000</td>
      <td>604000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1050</td>
      <td>910</td>
      <td>1965</td>
      <td>0</td>
      <td>98136</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360</td>
      <td>5000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>20150218T000000</td>
      <td>510000.0</td>
      <td>3</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1680</td>
      <td>0</td>
      <td>1987</td>
      <td>0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>21608</th>
      <td>263000018</td>
      <td>20140521T000000</td>
      <td>360000.0</td>
      <td>3</td>
      <td>2.50</td>
      <td>1530</td>
      <td>1131</td>
      <td>3.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1530</td>
      <td>0</td>
      <td>2009</td>
      <td>0</td>
      <td>98103</td>
      <td>47.6993</td>
      <td>-122.346</td>
      <td>1530</td>
      <td>1509</td>
    </tr>
    <tr>
      <th>21609</th>
      <td>6600060120</td>
      <td>20150223T000000</td>
      <td>400000.0</td>
      <td>4</td>
      <td>2.50</td>
      <td>2310</td>
      <td>5813</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>2310</td>
      <td>0</td>
      <td>2014</td>
      <td>0</td>
      <td>98146</td>
      <td>47.5107</td>
      <td>-122.362</td>
      <td>1830</td>
      <td>7200</td>
    </tr>
    <tr>
      <th>21610</th>
      <td>1523300141</td>
      <td>20140623T000000</td>
      <td>402101.0</td>
      <td>2</td>
      <td>0.75</td>
      <td>1020</td>
      <td>1350</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1020</td>
      <td>0</td>
      <td>2009</td>
      <td>0</td>
      <td>98144</td>
      <td>47.5944</td>
      <td>-122.299</td>
      <td>1020</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>21611</th>
      <td>291310100</td>
      <td>20150116T000000</td>
      <td>400000.0</td>
      <td>3</td>
      <td>2.50</td>
      <td>1600</td>
      <td>2388</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1600</td>
      <td>0</td>
      <td>2004</td>
      <td>0</td>
      <td>98027</td>
      <td>47.5345</td>
      <td>-122.069</td>
      <td>1410</td>
      <td>1287</td>
    </tr>
    <tr>
      <th>21612</th>
      <td>1523300157</td>
      <td>20141015T000000</td>
      <td>325000.0</td>
      <td>2</td>
      <td>0.75</td>
      <td>1020</td>
      <td>1076</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1020</td>
      <td>0</td>
      <td>2008</td>
      <td>0</td>
      <td>98144</td>
      <td>47.5941</td>
      <td>-122.299</td>
      <td>1020</td>
      <td>1357</td>
    </tr>
  </tbody>
</table>
<p>21613 rows × 21 columns</p>
</div>

