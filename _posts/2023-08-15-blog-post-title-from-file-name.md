### A bug when installing new environment in Conda
(base) atcold@AlfMAC3 ~ 
$ which python
/usr/local/bin/python  # system python
(base) atcold@AlfMAC3 ~ 
$ conda activate PPUU
(PPUU) atcold@AlfMAC3 ~ 
$ which python
/usr/local/bin/python  # still system python!
Workaround: run conda deactivate.

# Launching new shell
(base) atcold@AlfMAC3 ~ 
$ conda deactivate
atcold@AlfMAC3 ~ 
$ conda activate PPUU
(PPUU) atcold@AlfMAC3 ~ 
$ which python
/Users/atcold/opt/miniconda3/envs/PPUU/bin/python  # virtual environment python
(PPUU) atcold@AlfMAC3 ~ 
Seems like (base) needs to be deactivated first.
