# kaggle-JPX
[JPX Tokyo Stock Exchange Prediction](https://www.kaggle.com/competitions/jpx-tokyo-stock-exchange-prediction)のレポジトリ。  
本コンペでは入賞はできなかったが、新しく試したことから得られた学びが多かったため、作成したnotebookのうち、最終提出したnotebookと[https://arxiv.org/abs/2012.07245](https://arxiv.org/abs/2012.07245)の再現実装を行ったnotebookをgithubに挙げておく。


## spectral_residual.ipynb
[https://arxiv.org/abs/2012.07245](https://arxiv.org/abs/2012.07245)の再現実装を行ったnotebook。  
予測まで行えるようにはしたが、学習を進めていくとすべての銘柄に対しての予測値が同じになるようになってしまい、本コンペのデータではうまく機能しなかった。

## jpx-lightgbm-ranking-learning-final-sub.ipynb
LightGBMを用いたランキング学習による予測モデル。  
2000銘柄すべての順位付けを精度よく行うのは難しそうだったため、targetの値の良い順に順位付け、悪い順に順位付けし、それぞれの学習を行い、2つのモデルを作成。  
2つのモデルによる推論を行い、2つの推論結果をマージし、マージした結果によってランク付けを行った。これによって上位200位と下位200位のランク付けの精度が上がることを期待した。

## jpx-lightgbm-financials.ipynb
LightGBMでtargetの回帰予測を行うモデル。
日ごとの株価のデータおよびそこから得られるテクニカル指標などのデータに加え、財務諸表などから得られる各銘柄のファンダメンタルデータも特徴量として用いた。
