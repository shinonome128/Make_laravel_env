# README.md

## the purpose

Run php sample code with laravel framework

## references

[This]
(https://github.com/shinonome128/Make_laravel_env)

[vagrant + laravel]
(https://qiita.com/7968/items/97dd634608f37892b18a)

[laravel homestead]
(https://laravel.com/docs/5.1/homestead)

## ToDo

Step 2 Download Homestead vagrant box
Step 3 Download Homstead
Step 4 Create a configuration file for Laravel Homestead
Step 5 Create SSH key file
Step 6 Edit the Homestead Configuration File
Step 7 Start Virtual Machine
Step 8 Download Laravel file using Composer on virtual machine
Step 9 Display the Laravel page

## Step 2 Download Homestead vagrant box

    vagrant box add laravel/homestead

## Step 3 Download Homstead

    mkdir app
    cd ./app
    git clone https://github.com/laravel/homestead.git Homestead

## Step 4 Create a configuration file for Laravel Homestead

    bash init.sh

## Step 5 Create SSH key file
## Step 6 Edit the Homestead Configuration File

    mkdir code
    cd ./app/Homestead
    vim Homestead.yaml
    ```
    ip: "192.168.33.101"

    # authorize: ~/.ssh/id_rsa.pub
    #
    # keys:
    #     - ~/.ssh/id_rsa

    # - map: ~/code
    - map: ../../code
    ```

## Step 7 Start Virtual Machine

    cd ./app/Homestead
    vagrant up

## Step 8 Download Laravel file using Composer on virtual machine

on host

    vagrant ssh

on guest

    cd code/
    composer create-project laravel/laravel --prefer-dist Laravel

## Step 9 Display the Laravel page

アクセステスト
https://192.168.33.101
http://192.168.33.101

だめ
No input file specified.

    less /var/log/nginx/homestead.test-error.log

    2019/06/25 09:21:30 [error] 1148#1148: *1 FastCGI sent in stderr: "Unable to open primary script: /home/vagrant/code/public/index.php (No such file or directory)" while reading response header from upstream, client: 192.168.33.1, server: homestead.test, request: "GET / HTTP/1.1", upstream: "fastcgi://unix:/var/run/php/php7.3-fpm.sock:", host: "192.168.33.101"

fix yaml

    cd ./app/Homestead
    vim Homestead.yaml
    ```
      # to: /home/vagrant/code/public
      to: /home/vagrant/code/Laravel/public
    ```

    vagrant provision

## Register with Git

https://github.com/shinonome128/Make_laravel_env.git


    REPOSITORY=Make_laravel_env
    echo "# .gitignore" > .gitignore
    echo "DATA/" >> .gitignore
    echo "RESULT/" >> .gitignore
    echo "app/" >> .gitignore
    echo "code/" >> .gitignore
    echo "svn/" >> .gitignore
    echo ".svn/" >> .gitignore
    echo ".vagrant/" >> .gitignore
    echo ".DS_Store" >> .gitignore
    echo "__pycache__/" >> .gitignore
    echo "*.swp" >> .gitignore
    echo "*.result" >> .gitignore
    echo "*.sh" >> .gitignore
    echo "*.md" >> .gitignore
    echo "*.zip" >> .gitignore
    echo "*.tsv" >> .gitignore
    git init
    git config --local user.email shinonome128@gmail.com
    git config --local user.name "shinonome128"
    git add .gitignore
    git commit -m "Add first commit"
    git remote add origin https://github.com/shinonome128/$REPOSITORY.git
    git push -u origin master

EOF
