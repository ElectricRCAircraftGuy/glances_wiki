If you want to install Glances on a offline computer, you can follow this procedure.

On an **online computer**:

1. pip install basket
2. basket init
3. basket download glances
4. tar zcvf glances-offline.tgz .basket/*.*

Then copy the glances-offline.tgz file to your **offline computer** and:

1. cd ~
2. tar zxvf glances-offline.tgz
3. sudo mkdir /etc/glances
4. sudo touch /etc/glances/glances.conf

Install the Glances version with easy_install or pip:

*  sudo easy_install -f ~/.basket -H None glances

or

*  sudo pip install --no-index -f file://~/.basket glances

Thanks to Damien Baty for the Basket project.