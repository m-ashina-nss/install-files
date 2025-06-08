Gitサーバー（AWS EC2 Linux）用です。

①githab LFS化
git lfs install
git lfs track "*.tar"

②maven-image.tarの作成方法
git init
git lfs install
git lfs track "*.tar"
git add .\maven-image.tar
git add .gitattributes
git commit -m "add maven-image.tar"
git remote add origin https://github.com/m-ashina-nss/install-files.git
git push origin master
