If you want to install Glances on a offline computer, you can follow this procedure.

On an **online computer**:

1. pip install basket
2. basket init
3. basket download glances
4. tar zcvf glances-offline.tgz .basket/*.*

Copy the glances-offline.tgz file to your **offline computer** and...

**Install** the Glances version with easy_install or pip:

1. cd ~
2. tar zxvf glances-offline.tgz
3. sudo mkdir /etc/glances
4. sudo touch /etc/glances/glances.conf
5. sudo easy_install -f ~/.basket -H None glances
or sudo pip install --no-index -f file://~/.basket glances

**Upgrade** the Glances version with easy_install or pip:

1. cd ~
2. tar zxvf glances-offline.tgz
3. sudo mv /etc/glances /etc/glances.old
4. sudo mkdir /etc/glances
5. sudo touch /etc/glances/glances.conf
6. sudo easy_install --upgrade -f ~/.basket -H None glances
or sudo pip install --upgrade --no-index -f file://~/.basket glances

Edit your /etc/glances.glances.conf file (sample here: https://raw.githubusercontent.com/nicolargo/glances/master/conf/glances.conf)

Thanks to Damien Baty for the Basket project.