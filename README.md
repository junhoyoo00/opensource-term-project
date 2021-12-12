# opensource-term-project
#seoul_week_covid19


{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 313,
   "id": "a03664b5",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "8"
      ]
     },
     "execution_count": 313,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "import pandas as pd\n",
    "import matplotlib as mpl           \n",
    "import matplotlib.pyplot as plt    \n",
    "import numpy as np \n",
    "\n",
    "url=\"https://www.seoul.go.kr/coronaV/coronaStatus.do\"\n",
    "url\n",
    "\n",
    "table = pd.read_html(url)\n",
    "len(table)\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 314,
   "id": "87f89512",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>일자</th>\n",
       "      <th>12.11.</th>\n",
       "      <th>12.10.</th>\n",
       "      <th>12.9.</th>\n",
       "      <th>12.8.</th>\n",
       "      <th>12.7.</th>\n",
       "      <th>12.6.</th>\n",
       "      <th>12.5.</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>검사자(명)</td>\n",
       "      <td>104285.0</td>\n",
       "      <td>152569.0</td>\n",
       "      <td>151126.0</td>\n",
       "      <td>148171.0</td>\n",
       "      <td>141049.0</td>\n",
       "      <td>148597.0</td>\n",
       "      <td>73692.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>확진자(명)</td>\n",
       "      <td>2528.0</td>\n",
       "      <td>2835.0</td>\n",
       "      <td>2800.0</td>\n",
       "      <td>2790.0</td>\n",
       "      <td>2901.0</td>\n",
       "      <td>2120.0</td>\n",
       "      <td>1408.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>확진율(%)</td>\n",
       "      <td>1.7</td>\n",
       "      <td>1.9</td>\n",
       "      <td>1.9</td>\n",
       "      <td>2.0</td>\n",
       "      <td>2.0</td>\n",
       "      <td>2.9</td>\n",
       "      <td>1.4</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "       일자    12.11.    12.10.     12.9.     12.8.     12.7.     12.6.    12.5.\n",
       "0  검사자(명)  104285.0  152569.0  151126.0  148171.0  141049.0  148597.0  73692.0\n",
       "1  확진자(명)    2528.0    2835.0    2800.0    2790.0    2901.0    2120.0   1408.0\n",
       "2  확진율(%)       1.7       1.9       1.9       2.0       2.0       2.9      1.4"
      ]
     },
     "execution_count": 314,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df=table[3]\n",
    "df\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 346,
   "id": "2b445a09",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>0</th>\n",
       "      <th>1</th>\n",
       "      <th>2</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>일자</th>\n",
       "      <td>검사자(명)</td>\n",
       "      <td>확진자(명)</td>\n",
       "      <td>확진율(%)</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.11.</th>\n",
       "      <td>104285.0</td>\n",
       "      <td>2528.0</td>\n",
       "      <td>1.7</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.10.</th>\n",
       "      <td>152569.0</td>\n",
       "      <td>2835.0</td>\n",
       "      <td>1.9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.9.</th>\n",
       "      <td>151126.0</td>\n",
       "      <td>2800.0</td>\n",
       "      <td>1.9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.8.</th>\n",
       "      <td>148171.0</td>\n",
       "      <td>2790.0</td>\n",
       "      <td>2.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.7.</th>\n",
       "      <td>141049.0</td>\n",
       "      <td>2901.0</td>\n",
       "      <td>2.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.6.</th>\n",
       "      <td>148597.0</td>\n",
       "      <td>2120.0</td>\n",
       "      <td>2.9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.5.</th>\n",
       "      <td>73692.0</td>\n",
       "      <td>1408.0</td>\n",
       "      <td>1.4</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "               0       1       2\n",
       "일자        검사자(명)  확진자(명)  확진율(%)\n",
       "12.11.  104285.0  2528.0     1.7\n",
       "12.10.  152569.0  2835.0     1.9\n",
       "12.9.   151126.0  2800.0     1.9\n",
       "12.8.   148171.0  2790.0     2.0\n",
       "12.7.   141049.0  2901.0     2.0\n",
       "12.6.   148597.0  2120.0     2.9\n",
       "12.5.    73692.0  1408.0     1.4"
      ]
     },
     "execution_count": 346,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ddf=df.T\n",
    "ddf"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 321,
   "id": "79070c1a",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>12.11.</th>\n",
       "      <th>12.10.</th>\n",
       "      <th>12.9.</th>\n",
       "      <th>12.8.</th>\n",
       "      <th>12.7.</th>\n",
       "      <th>12.6.</th>\n",
       "      <th>12.5.</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>104285.0</td>\n",
       "      <td>152569.0</td>\n",
       "      <td>151126.0</td>\n",
       "      <td>148171.0</td>\n",
       "      <td>141049.0</td>\n",
       "      <td>148597.0</td>\n",
       "      <td>73692.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>2528.0</td>\n",
       "      <td>2835.0</td>\n",
       "      <td>2800.0</td>\n",
       "      <td>2790.0</td>\n",
       "      <td>2901.0</td>\n",
       "      <td>2120.0</td>\n",
       "      <td>1408.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>1.7</td>\n",
       "      <td>1.9</td>\n",
       "      <td>1.9</td>\n",
       "      <td>2.0</td>\n",
       "      <td>2.0</td>\n",
       "      <td>2.9</td>\n",
       "      <td>1.4</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "     12.11.    12.10.     12.9.     12.8.     12.7.     12.6.    12.5.\n",
       "0  104285.0  152569.0  151126.0  148171.0  141049.0  148597.0  73692.0\n",
       "1    2528.0    2835.0    2800.0    2790.0    2901.0    2120.0   1408.0\n",
       "2       1.7       1.9       1.9       2.0       2.0       2.9      1.4"
      ]
     },
     "execution_count": 321,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "sdf=df.drop(['일자'],axis=1)\n",
    "sdf"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 319,
   "id": "c19ab3f3",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>검사자(명)</th>\n",
       "      <th>확진자(명)</th>\n",
       "      <th>확진율(%)</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>12.11.</th>\n",
       "      <td>104285.0</td>\n",
       "      <td>2528.0</td>\n",
       "      <td>1.7</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.10.</th>\n",
       "      <td>152569.0</td>\n",
       "      <td>2835.0</td>\n",
       "      <td>1.9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.9.</th>\n",
       "      <td>151126.0</td>\n",
       "      <td>2800.0</td>\n",
       "      <td>1.9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.8.</th>\n",
       "      <td>148171.0</td>\n",
       "      <td>2790.0</td>\n",
       "      <td>2.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.7.</th>\n",
       "      <td>141049.0</td>\n",
       "      <td>2901.0</td>\n",
       "      <td>2.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.6.</th>\n",
       "      <td>148597.0</td>\n",
       "      <td>2120.0</td>\n",
       "      <td>2.9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>12.5.</th>\n",
       "      <td>73692.0</td>\n",
       "      <td>1408.0</td>\n",
       "      <td>1.4</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "          검사자(명)  확진자(명)  확진율(%)\n",
       "12.11.  104285.0  2528.0     1.7\n",
       "12.10.  152569.0  2835.0     1.9\n",
       "12.9.   151126.0  2800.0     1.9\n",
       "12.8.   148171.0  2790.0     2.0\n",
       "12.7.   141049.0  2901.0     2.0\n",
       "12.6.   148597.0  2120.0     2.9\n",
       "12.5.    73692.0  1408.0     1.4"
      ]
     },
     "execution_count": 319,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ssdf=sdf.T\n",
    "ssdf.columns=('검사자(명)','확진자(명)','확진율(%)')\n",
    "ssdf\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "8adec3ec",
   "metadata": {},
   "outputs": [],
   "source": [
    "pd.melt()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 355,
   "id": "c818cc07",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "검사자(명)    104285.0\n",
       "확진자(명)      2528.0\n",
       "확진율(%)         1.7\n",
       "Name: 12.11., dtype: float64"
      ]
     },
     "execution_count": 355,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "s1df = ssdf.loc['12.11.']\n",
    "type(s1df)\n",
    "s1df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 356,
   "id": "c458e0cc",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "검사자(명)    152569.0\n",
       "확진자(명)      2835.0\n",
       "확진율(%)         1.9\n",
       "Name: 12.10., dtype: float64"
      ]
     },
     "execution_count": 356,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "s2df = ssdf.loc['12.10.']\n",
    "s2df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 357,
   "id": "007eec68",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "검사자(명)    151126.0\n",
       "확진자(명)      2800.0\n",
       "확진율(%)         1.9\n",
       "Name: 12.9., dtype: float64"
      ]
     },
     "execution_count": 357,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "s3df = ssdf.loc['12.9.']\n",
    "s3df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 358,
   "id": "6112fa2b",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "검사자(명)    148171.0\n",
       "확진자(명)      2790.0\n",
       "확진율(%)         2.0\n",
       "Name: 12.8., dtype: float64"
      ]
     },
     "execution_count": 358,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "s4df = ssdf.loc['12.8.']\n",
    "s4df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 359,
   "id": "e23b142f",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "검사자(명)    141049.0\n",
       "확진자(명)      2901.0\n",
       "확진율(%)         2.0\n",
       "Name: 12.7., dtype: float64"
      ]
     },
     "execution_count": 359,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "s5df = ssdf.loc['12.7.']\n",
    "s5df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 360,
   "id": "c9d34a02",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "검사자(명)    148597.0\n",
       "확진자(명)      2120.0\n",
       "확진율(%)         2.9\n",
       "Name: 12.6., dtype: float64"
      ]
     },
     "execution_count": 360,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "s6df = ssdf.loc['12.6.']\n",
    "s6df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 361,
   "id": "a116f04b",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "검사자(명)    73692.0\n",
       "확진자(명)     1408.0\n",
       "확진율(%)        1.4\n",
       "Name: 12.5., dtype: float64"
      ]
     },
     "execution_count": 361,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "s7df = ssdf.loc['12.5.']\n",
    "s7df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 362,
   "id": "54aa7e43",
   "metadata": {},
   "outputs": [],
   "source": [
    "filename0=\"seoul_week_covid19.csv\"\n",
    "ssdf.to_csv(filename0,index=True)\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 363,
   "id": "991cbe16",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Unnamed: 0</th>\n",
       "      <th>검사자(명)</th>\n",
       "      <th>확진자(명)</th>\n",
       "      <th>확진율(%)</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>12.11.</td>\n",
       "      <td>104285.0</td>\n",
       "      <td>2528.0</td>\n",
       "      <td>1.7</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>12.10.</td>\n",
       "      <td>152569.0</td>\n",
       "      <td>2835.0</td>\n",
       "      <td>1.9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>12.9.</td>\n",
       "      <td>151126.0</td>\n",
       "      <td>2800.0</td>\n",
       "      <td>1.9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>12.8.</td>\n",
       "      <td>148171.0</td>\n",
       "      <td>2790.0</td>\n",
       "      <td>2.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>12.7.</td>\n",
       "      <td>141049.0</td>\n",
       "      <td>2901.0</td>\n",
       "      <td>2.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>5</th>\n",
       "      <td>12.6.</td>\n",
       "      <td>148597.0</td>\n",
       "      <td>2120.0</td>\n",
       "      <td>2.9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>6</th>\n",
       "      <td>12.5.</td>\n",
       "      <td>73692.0</td>\n",
       "      <td>1408.0</td>\n",
       "      <td>1.4</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "  Unnamed: 0    검사자(명)  확진자(명)  확진율(%)\n",
       "0     12.11.  104285.0  2528.0     1.7\n",
       "1     12.10.  152569.0  2835.0     1.9\n",
       "2      12.9.  151126.0  2800.0     1.9\n",
       "3      12.8.  148171.0  2790.0     2.0\n",
       "4      12.7.  141049.0  2901.0     2.0\n",
       "5      12.6.  148597.0  2120.0     2.9\n",
       "6      12.5.   73692.0  1408.0     1.4"
      ]
     },
     "execution_count": 363,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "pd.read_csv(filename0)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 364,
   "id": "35fe4309",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "검사자(명)    131355.571429\n",
       "확진자(명)      2483.142857\n",
       "확진율(%)         1.971429\n",
       "dtype: float64"
      ]
     },
     "execution_count": 364,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ssdf.mean(axis=0)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 365,
   "id": "cbabc099",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "[<matplotlib.lines.Line2D at 0x1d8af03c430>]"
      ]
     },
     "execution_count": 365,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "fig=plt.figure()\n",
    "axes1=fig.add_subplot(1,7,1)\n",
    "axes1.plot(s1df['검사자(명)'],s1df['확진자(명)'],'o')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 374,
   "id": "e43a91fd",
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 7 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "fig=plt.figure()\n",
    "axes1=fig.add_subplot(3,3,1)\n",
    "axes2=fig.add_subplot(3,3,2)\n",
    "axes3=fig.add_subplot(3,3,3)\n",
    "axes4=fig.add_subplot(3,3,4)\n",
    "axes5=fig.add_subplot(3,3,5)\n",
    "axes6=fig.add_subplot(3,3,6)\n",
    "axes7=fig.add_subplot(3,3,7)\n",
    "\n",
    "axes1.plot(s7df['검사자(명)'],s7df['확진자(명)'],'o')\n",
    "axes2.plot(s6df['검사자(명)'],s6df['확진자(명)'],'o')\n",
    "axes3.plot(s5df['검사자(명)'],s5df['확진자(명)'],'o')\n",
    "axes4.plot(s4df['검사자(명)'],s4df['확진자(명)'],'o')\n",
    "axes5.plot(s3df['검사자(명)'],s3df['확진자(명)'],'o')\n",
    "axes6.plot(s2df['검사자(명)'],s2df['확진자(명)'],'o')\n",
    "axes7.plot(s1df['검사자(명)'],s1df['확진자(명)'],'o')\n",
    "\n",
    "fig.suptitle('seoul_week_covid19')\n",
    "axes1.set_title(12.5)\n",
    "axes2.set_title(12.6)\n",
    "axes3.set_title(12.7)\n",
    "axes4.set_title(12.8)\n",
    "axes5.set_title(12.9)\n",
    "axes6.set_title(12.10)\n",
    "axes7.set_title(12.11)\n",
    "fig.tight_layout()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "e2f1f82d",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.7"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
