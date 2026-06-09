# improve-ukt-
improve ukt
创建环境
```
conda create --name=ukt python=3.7.5
conda activate ukt
```

安装依赖包
```
pip install -U pykt-toolkit -i  https://pypi.python.org/simple 
```

进入文件
```
cd UKT-main
cd train
```

处理数据集的数据
```
python data_preprocess.py --dataset_name=assist2009
```

跑代码
```
CUDA_VISIBLE_DEVICES=0 python wandb_ukt_train.py --fold=0 --emb_type=qid --loss3=0.5 --d_ff=64   --nheads=4 --dropout=0.1 --loss2=0.5 --final_fc_dim2=256 --loss1=0.5 --d_model=256 --num_attn_heads=4 --num_layers=2 --seed=42    --final_fc_dim=512 --n_blocks=4 --start=50 --learning_rate=0.0001  --dataset_name=assist2009 --emb_type='stoc_qid' --atten_type='w2'
```

使用模型saved_model/YourModelPath填入实际的路径
```
python wandb_predict.py --save_dir=saved_model/YourModelPath
```

