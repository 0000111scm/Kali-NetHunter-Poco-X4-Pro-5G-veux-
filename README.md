# Kali-NetHunter Poco-X4-Pro-5G (veux) 

🚀 Base: Android 16 | EvolutionX | Nebula Kernel | KernelSU

Este guia documenta a instalação funcional e estável do Kali NetHunter no Poco X4 Pro 5G (veux), validado na base Android 16.

⚠️ AVISO / DISCLAIMER
Eu não me responsabilizo por travamentos, loops infinitos ou qualquer problema no seu aparelho. Eu sou apenas um curioso com um celular para testar as coisas. Siga este guia por sua conta e risco. É altamente recomendável fazer backup antes de começar.

📊 Especificações do Setup Validado
Aparelho: Poco X4 Pro 5G (veux)

ROM: EvolutionX 16.0 (Android 16)

Recovery: EvolutionX Recovery (Oficial)

Kernel: Nebula Kernel r07 (v5.4.293)

Root: KernelSU (v1.0.5-61)

SELinux: Permissivo (Permissive)

⚠️ Nota sobre o KernelSU
Para evitar conflitos de permissão no Android 16, utilize preferencialmente a build 12998 ou inferior do gerenciador. Versões muito recentes podem causar falhas na montagem do chroot.

📋 Pré-requisitos e Preparação
No Computador:
Drivers ADB e Fastboot instalados.

Cabo USB de boa qualidade.

No Celular:
Bootloader Desbloqueado (Obrigatório).

Ativar Modo Desenvolvedor: Vá em Configurações > Sobre o Telefone e toque 7 vezes em Número da Versão.

Ativar Depuração USB: Em Sistema > Opções do Desenvolvedor, ative a Depuração USB.

Custom ROM: Recomendado uso de ROMs AOSP (Guia validado na EvolutionX 16.0).

📡 Hardware Wi-Fi usado: Atheros AR9271
O setup oferece suporte "Plug and Play" para a antena TP-Link TL-WN722N v1.

Chipset: Atheros AR9271 (Suporte nativo para Modo Monitor + Injeção).

Identificação: Identificado no terminal via lsusb como ID 0cf3:9271.

🛠️ Procedimento de Instalação
1. Partições Base (Fastboot)
Com o celular em modo Fastboot, flashe as partições para garantir compatibilidade com o kernel:

Bash
fastboot flash boot boot.img
fastboot flash vendor_boot vendor_boot.img
fastboot flash dtbo dtbo.img
2. Limpeza e Instalação da ROM (Recovery)
Reinicie o aparelho no Recovery Mode.

Vá em Factory Reset > Format Data/Factory Reset (Atenção: isso apagará tudo).

Retorne ao menu principal e selecione Apply Update > Apply from ADB.

No computador, execute o comando para instalar a ROM:

Bash
adb sideload nome_da_sua_rom.zip
(Aguarde a conclusão total da instalação da ROM antes de avançar).

3. Flash do Kernel (Sideload)
Ainda no Recovery (ou acessando novamente Apply from ADB), instale o kernel:

Bash
adb sideload Nebula-Kernel-r07-veux.zip
Após o término, selecione Reboot System Now para iniciar o Android.

4. NetHunter Chroot
Após o sistema iniciar, instale o KernelSU, o NetHunter Store e baixe os apps NetHunter e NetHunter Terminal.

⚠️ IMPORTANTE: Antes de abrir os aplicativos, vá ao app do KernelSU e conceda permissão de Superusuário (Root) manualmente para o NetHunter e para o NetHunter Terminal.

Abra o App NetHunter, vá em Kali Chroot Manager e realize a instalação do Chroot.

Após finalizar, abra o terminal e atualize os pacotes:

Bash
apt update && apt upgrade -y
