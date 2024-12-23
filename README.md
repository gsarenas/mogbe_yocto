# mogbe_yocto

Manifest para fazer a build da imagem de Linux com ROS 2 para o MOGBE usando Yocto Project.

1. Configurando a ferramenta repo (Google):

```bash
mkdir ~/bin
```

```bash
PATH=~/bin:$PATH
```

```bash
curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
```

```bash
chmod a+x ~/bin/repo
```

2. Criando nossa área de trabalho:

```bash
mkdir -p ~/mogbe/yocto && cd ~/mogbe/yocto
```

Ajuste o branch se necessário:
```bash
repo init git@github.com:gsarenas/mogbe_yocto.git -b scarthgap
```

```bash
repo sync
```

<!-- > [!IMPORTANT] -->  
<!-- > É importante ter configurado a chave SSH do GitHub para clonar a `meta-mogbe`. -->

> Note que o repositório `Poky` foi extraído em `layers` diretamente.

3. Com isso, basta configurar as variáveis de ambiente:

```bash
. setup-yocto
```

4. Você deve ser redirecionado ao diretório de build. A nova estrutura da nossa área de trabalho com as novas adições deve ser assim:

```plaintext
.
├── build/
│   └── conf/
│       ├── bblayers.conf
│       ├── conf-notes.txt
│       ├── conf-summary.txt
│       ├── local.conf
│       └── templateconf.cfg
├── layers/
└── setup-yocto
```

> Note que o `bblayers.conf` e `local.conf` devem vir pré-configurados.

6. Para fazer a build, basta rodar:

```bash
bitbake mogbe-ros2
```
