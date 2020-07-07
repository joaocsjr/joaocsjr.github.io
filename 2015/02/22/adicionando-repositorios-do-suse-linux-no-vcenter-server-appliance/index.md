# Adicionando repositórios do SUSE Linux no Vcenter Server Appliance


Com o uso do VCSA (Vcenter Server Appliance), algumas ferramentas Linux podem ser uteis em um troubleshooting, como por exemplo o htop que é uma ferramenta muito útil para análise de performance em servidores Linux, para podermos instalar no Vcenter precisamos adicionar os repositórios do SUSE Linux nele, vamos lá:

Vamos adicionar o repositório com o comando abaixo:

<!-- more -->
``` bash
**# sudo zypper --gpg-auto-import-keys ar http://download.opensuse.org/distribution/11.1/repo/oss/ 11.1
**

_Adding repository '11.1' [done]
_

_Repository '11.1' successfully added
_

_Enabled: Yes
_

_Autorefresh: No
_

_GPG check: Yes
_

_URI: [http://download.opensuse.org/distribution/11.1/repo/oss/](http://download.opensuse.org/distribution/11.1/repo/oss/)
_

**#sudo zypper --gpg-auto-import-keys ar http://download.opensuse.org/update/11.1/ Update-11**.1


_Adding repository 'Update-11.1' [done]
_

_Repository 'Update-11.1' successfully added
_

_Enabled: Yes
_

_Autorefresh: No
_

_GPG check: Yes
_

_URI: [http://download.opensuse.org/update/11.1/](http://download.opensuse.org/update/11.1/)
_

Validando se os repositórios foram adicionados:


**#zypper lr
**

_# | Alias | Name | Enabled | Refresh
_

_--+-------------+-------------+---------+--------
_

_1 | 11.1 | 11.1 | Yes | No
_

_2 | Update-11.1 | Update-11.1 | Yes | No
_

_Após adicionarmos os repositórios precisamos dar um refresh para que a lista de pacotes disponíveis possam ser atualizadas:
_

**#sudo zypper refresh
**

_Retrieving repository '11.1' metadata [-]
_

_New repository or package signing key received:
_

_Key ID: B88B2FD43DBDC284
_

_Key Name: openSUSE Project Signing Key <opensuse@opensuse.org>
_

_Key Fingerprint: 22C07BA534178CD02EFE22AAB88B2FD43DBDC284
_

_Key Created: Fri Nov 7 14:10:07 2008
_

_Key Expires: Sun Nov 7 14:10:07 2010 (EXPIRED)
_

_Repository: 11.1
_

_Do you want to reject the key, trust temporarily, or trust always? [r/t/a/?] (r): a
_

_Retrieving repo Retrieving repository '11.1' metadata [done]
_

_Building repository '11.1' cache [done]
_

_Retrieving repo sitory 'Update- Retrieving repository 'Update-11.1' metadata [done]
_

_Building repository 'Update-11.1' cache [done]
_

_All repositories have been refreshed.
_

_Instalando o Htop:
_

**sudo zypper install htop
**

_Loading repository data...
_

_Warning: Repository 'Update-11.1' appears to outdated. Consider using a different mirror or server.
_

_Reading installed packages...
_

_Resolving package dependencies...
_

_The following NEW package is going to be installed:
_

_ htop
_

_1 new package to install.
_

_Overall download size: 56.0 KiB. After the operation, additional 123.0 KiB will be used.
_

_Continue? [y/n/?] (y): y
_

_Retrieving package htop-0.8.1-2.5.x86_64 (1/1), 56.0 KiB (123.0 KiB unpacked)
_

_Retrieving: htop-0.8.1-2.5.x86_64.rpm [done (10.6 KiB/s)]
_

_Installing: htop-0.8.1-2.5 [done]
_

_
_
```

