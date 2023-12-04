## Create conda environment
```
conda create --name python-sql python=3.8

proceed ([y]/n)? y
```

## Activate environment
```
conda activate python-sql
```
## Install yum requirements
```
sudo yum -y groupinstall "Development Tools"
sudo yum -y install python3-devel
sudo yum -y install postgresql-libs
sudo yum -y install postgresql-devel
```

## Install pip requirements
```
 pip install jupyterlab sqlalchemy pandas psycopg2
```

## Jupyter kernel
` ipython kernel install --user --name=python-sql `

## Start Jupyter Lab
- Start  
` jupyter lab --ip 0.0.0.0 --port 8990 `

- Copy link  
` http://127.0.0.1:8990/lab?token=d137758b0014e1745f1946a91083e1256be7ff9051a4a95c `


## Remove conda env 
` conda env remove -n python-sql ` 