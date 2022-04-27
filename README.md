# utilLinks

<p align="left">
NVM-Windows: https://github.com/coreybutler/nvm-windows/releases <br />
Docker-Compose: https://docs.docker.com/compose/gettingstarted/ <br />
Install mongodb-Shell: https://www.mongodb.com/try/download/shell <br />
Erro do ubuntu busybox e initramfs: https://www.webtutorial.com.br/erro-ao-inicializar-o-linux-ubuntu-busybox-e-initramfs/ <br />
Erro do ubuntu apt-update: https://virtuakeoblog.wordpress.com/2019/02/22/como-resolver-o-erro-impossivel-analisar-arquivo-de-pacote-var-lib-apt-extended_states-1-no-ubuntu/ <br />
Querys MySql to Mongo: https://www.mongodb.com/docs/manual/reference/sql-comparison/
</p>

## resolução travada em 640x480

Com uma das distribuições indicadas instalada em seu computador, vamos forçar o Xorg a aumentar a resolução de vídeo.

Gere o arquivo de configurações do xorg.

    sudo Xorg :1 -configure

Abra o arquivo gerado para poder fazer as alterações.

    sudo nano /root/xorg.conf.new

localize

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Viewport 0 0
Depth 1
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Altere para:

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
Subsection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "600x400"
EndSubsection
Subsection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "600x400"
EndSubsection
Subsection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "600x400"
EndSubsection
Subsection "Display"
Depth 32
Modes "1280x1024" "1024x768" "800x600" "600x400"
EndSubSection
EndSection

Salve teclando Ctrl + x tecle s e tecle Enter para fechar.

Copie o arquivo alterado para /etc/X11/ com o comando.

    sudo cp /root/xorg.conf.new /etc/X11/xorg.conf

Reinicie o computador para testar.

    sudo reboot

OBS: Caso não abra a interface gráfica e fique em uma tela preta, remova o arquivo que criamos.

Tecle Ctrl + Alt + f2

Log com seu usuário.

Remova o arquivo com o comando abaixo.

    sudo rm -fr /etc/X11/xorg.conf

Reinicie o computador.

    sudo reboot

