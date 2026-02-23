# Kali-NetHunter Poco-X4-Pro-5G (veux) 

🚀 **Base: Android 16 | EvolutionX | Nebula Kernel | KernelSU**

Este guia documenta a instalação funcional e estável do Kali NetHunter no **Poco X4 Pro 5G (veux)**, validado na base Android 16.

---

### ⚠️ AVISO / DISCLAIMER
**Eu não me responsabilizo por travamentos, loops infinitos ou qualquer problema no seu aparelho.** Eu sou apenas um curioso com um celular para testar as coisas. Siga este guia por sua conta e risco. **É altamente recomendável fazer backup antes de começar.**

---

## 📊 Especificações do Setup Validado
* **Aparelho:** Poco X4 Pro 5G (veux)
* **ROM:** EvolutionX 16.0 (Android 16)
* **Recovery:** EvolutionX Recovery (Oficial)
* **Kernel:** Nebula Kernel r07 (v5.4.293)
* **Root:** KernelSU (v1.0.5-61)
* **SELinux:** Permissivo (Permissive)

---

## 📋 Pré-requisitos e Preparação
### No Computador:
* Drivers **ADB e Fastboot** instalados.
* Cabo USB de boa qualidade.

### No Celular:
* **Bootloader Desbloqueado** (Obrigatório).
* **Ativar Modo Desenvolvedor:** Vá em *Configurações > Sobre o Telefone* e toque 7 vezes em *Número da Versão*.
* **Ativar Depuração USB:** Em *Sistema > Opções do Desenvolvedor*, ative a **Depuração USB**.

---

## 🛠️ Procedimento de Instalação

### 1. Partições Base (Fastboot)
Com o celular em modo Fastboot, flashe as partições para garantir compatibilidade com o kernel:

```bash
fastboot flash boot boot.img
fastboot flash vendor_boot vendor_boot.img
fastboot flash dtbo dtbo.img
```

---

### 2. Limpeza e Instalação da ROM (Recovery)
1. Reinicie o aparelho no **Recovery Mode**.
2. Vá em **Factory Reset** > **Format Data/Factory Reset** (Atenção: isso apagará tudo).
3. Retorne ao menu principal e selecione **Apply Update** > **Apply from ADB**.
4. No computador, execute o comando para instalar a ROM:

```bash
adb sideload nome_da_sua_rom.zip
```
### 3. Flash do Kernel (Sideload)
Ainda no Recovery (ou acessando novamente **Apply from ADB**), instale o kernel:

```bash
adb sideload Nebula-Kernel-r07-veux.zip
```
4. NetHunter Chroot
Após o sistema iniciar, instale o KernelSU, o NetHunter Store e baixe os apps NetHunter e NetHunter Terminal.

⚠️ IMPORTANTE: Antes de abrir os aplicativos, vá ao app do KernelSU e conceda permissão de Superusuário (Root) manualmente para o NetHunter e para o NetHunter Terminal.

Abra o App NetHunter, vá em Kali Chroot Manager e realize a instalação do Chroot.

Após finalizar, abra o terminal do Kali e atualize os pacotes:
```bash
apt update && apt upgrade -y
```

