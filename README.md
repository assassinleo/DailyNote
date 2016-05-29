# DailyNote

### Daily Note for reference
===========
***
2016.5.29

* 1.pip install packages from local

use below command:
(DIR include packages(wheel, soure) you want to install)
> pip install --no-index --find-links=DIR -r requirements.txt

ref: https://pip.pypa.io/en/stable/user_guide/#installing-from-local-packages

* 2.virtualenv usage:

```pip install virtualenv
virtualenv --no-site-packages venv
cd venv
source venv/bin/activate
deactivate
```

ref: http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001432712108300322c61f256c74803b43bfd65c6f8d0d0000