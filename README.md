# LIUYUHAN
Mathematic statistics
import pandas as pd
import sys,os
import numpy as np
from pandas import Series,DataFrame
import matplotlib.pyplot as plt

os.chdir(os.path.dirname('/Users/liuyuhan9322/anaconda/2017dataset/guest.csv'))
guest = pd.read_csv(os.path.basename('/Users/liuyuhan9322/anaconda/2017dataset/guest.csv'),encoding="SHIFT-JIS")
print('顧客:',guest.shape,type(guest))

os.chdir(os.path.dirname('/Users/liuyuhan9322/anaconda/2017dataset/receipt1.csv'))
receipt1 = pd.read_csv(os.path.basename('/Users/liuyuhan9322/anaconda/2017dataset/receipt1.csv'),encoding="SHIFT-JIS")
print('会計履歴:',receipt1.shape,type(receipt1))

os.chdir(os.path.dirname('/Users/liuyuhan9322/anaconda/2017dataset/receipt2.csv'))
receipt2 = pd.read_csv(os.path.basename('/Users/liuyuhan9322/anaconda/2017dataset/receipt2.csv'),encoding="SHIFT-JIS",low_memory=False)
print('会計明細:',receipt2.shape)

os.chdir(os.path.dirname('/Users/liuyuhan9322/anaconda/2017dataset/master.csv'))
master = pd.read_csv(os.path.basename('/Users/liuyuhan9322/anaconda/2017dataset/master.csv'),encoding="SHIFT-JIS")
print('担当者：',master.shape)

os.chdir(os.path.dirname('/Users/liuyuhan9322/anaconda/2017dataset/shop.csv'))
shop = pd.read_csv(os.path.basename('/Users/liuyuhan9322/anaconda/2017dataset/shop.csv'),encoding="SHIFT-JIS")
print('店舗：',shop.shape)

import codecs
with codecs.open("goods.csv",'r', "Shift-JIS", "ignore") as csv_file:
    goods = pd.read_csv(csv_file)
print('商品:', goods.shape)

unit_def1=pd.merge(goods_def,receipt2_def) #.set_index(['会計ID'])
unit_def2=pd.merge(receipt1_def,guest_def) #.set_index(['顧客ID','会計ID'])
unit_def3=pd.merge(unit_def1,unit_def2) #left_index=True,right_index=True)
unit_def=unit_def3.set_index(['顧客ID','会計ID'])
unit_def
