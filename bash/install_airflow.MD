다른유저로 install 쉘을실행 
```
user runuser -l ec2-user -c /path/to/below/scripte.sh
``` 

```
#!/bin/bash

set -e

sudo yum install git

sudo yum install curl

curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash

# 'EOF'는 here-document 스펙으로 cat ~ EOF내 명령들을 litter로 다룬다.
cat <<'EOF' >> ~/.bashrc
  export PATH="/home/ec2-user/.pyenv/bin:$PATH"
  eval "$(pyenv init -)"
  eval "$(pyenv virtualenv-init -)"
EOF

source ~/.bashrc

sudo yum install zlib-devel bzip2 bzip2-devel readline-devel sqlite sqlite-devel openssl-devel xz xz-devel libffi-devel

sudo yum install gcc-c++

pyenv install 3.7.1

pyenv global 3.7.1

python --version

pip install --upgrade pip

sudo yum install python-devel mysql-devel

export AIRFLOW_HOME=/services/apps/airflow

export SLUGIFY_USES_TEXT_UNIDECODE=yes

pip install apache-airflow[celery,jdbc,devel,slack]


airflow initdb
airflow webserver -p 8080 -D
airflow scheduler -D
```
