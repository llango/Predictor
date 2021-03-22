## 后端操作
### 步骤:

1. 克隆这个Github。
2. 创建虚拟环境 `python -m venv env`
3. 激活环境 `source env/bin/activate`
4. 安装 `pip install -r requirements.txt`

### 创建超级用户
`python manage.py createsuper`

### 收集静态文件
`python manage.py collectstatic`

### 运行
`python manage.py runserver`

## 前端操作
1. 进入vue/heart
2. 安装依赖 yarn install / npm install
3. 运行 yarn run serve  / npm run serve


## ML操作
1. 打开vscode 或 jupyterlab 或 notebook
2. 直接一步一步运行便可。


## 注意的地方
文件路径需要进行修改：涉及的文件路径有：
ML 目录下的heart-notebook.ipynb 应用的文件 `/Users/zou/development/aiproject/Predictor/ML/new_model.pickle` 改成ML目录对应你的绝对路径。
djangoapi/heartapi views.py 下的路径同样得修改。
