# Git #
## github with atom #
- Github中创建仓库（项目）
- Github中拷贝Clone/Download的URL
- 命令行：git clone URL
  - git clone https://github.com/username/project.git
- Atom中添加本地项目路径，添加、更新文件
- 命令行：git status
  - git add file
  - git commit -m "message"
  - git push

## git 配置
- git config --list
- git config --global user.name "username"
- git config --global user.email "emailaddress"

## git ssh配置
- 打开git Bash
- git 配置name和email
- cd ~/.ssh 如果.ssh目录下有三个文件，则密钥已经生成，否则需要生成密钥
- 可通过如下方式生成密钥
  - ssh-keygen -t rsa -C "emailaddress"
  - 生成过程默认方式。（默认路径，默认没有密码登录）
  - 生成成功后，一般在目录：C:/users/name/.ssh/id_rsa
- 使用记事本打开id_rsa.pub，得到ssh key公钥。
- 在github，点开settings，打开“SSH and PGP keys”，点击“New SSH Key”
