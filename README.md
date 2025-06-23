# Bread
🖥️ 1. Configuração de Energia e Sistema:
Plano de Energia Customizado (Máxima Performance Real):

👉 CMD como admin:

cmd
Copiar
Editar
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
👉 Depois:

Painel de Controle > Energia > Selecione o "Ultimate Performance"

⚠️ Opcional: Desative suspensão de HD, USB e PCI Express no plano de energia.

🎛️ 2. Desativação Total de Bloatware, Apps Inúteis e Telemetria:
Remova Apps da Microsoft:

👉 PowerShell como Admin:

powershell
Copiar
Editar
Get-AppxPackage *xbox* | Remove-AppxPackage
Get-AppxPackage *cortana* | Remove-AppxPackage
Get-AppxPackage *bing* | Remove-AppxPackage
Get-AppxPackage *solitaire* | Remove-AppxPackage
Desativar Telemetria via Regedit:

reg
Copiar
Editar
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\DataCollection]
"AllowTelemetry"=dword:00000000
Bloquear Serviços de Telemetria por IP (via Hosts ou Firewall):

👉 Bloqueie domínios como:

vortex.data.microsoft.com

settings-win.data.microsoft.com

⚡ 3. Cortando o Windows Update pela Raiz (se quiser):
👉 Services.msc:

Windows Update > Desativado

👉 Regedit (desligamento forçado):

reg
Copiar
Editar
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\wuauserv]
"Start"=dword:00000004
🧬 4. Regedit Tweaks Avançados (Latency + FPS):
Disable Fullscreen Optimizations + GPU Scheduling:

👉 Propriedades de cada jogo > Compatibilidade > Marcar "Desativar Otimizações de Tela Cheia"

👉 Ative Hardware-Accelerated GPU Scheduling:

Configurações > Sistema > Exibir > Configurações Gráficas

Latency Mode NVIDIA/AMD:
👉 No painel da GPU: Low Latency Mode: Ultra (NVIDIA) ou equivalente na AMD.

Win32PrioritySeparation: (Melhor foco em foreground)

reg
Copiar
Editar
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\PriorityControl]
"Win32PrioritySeparation"=dword:00000026
Desligar Sleep States (C-States) e CPU Throttling (se possível na BIOS):

👉 Entre na BIOS:

Desative:

C1E

Intel SpeedStep (ou Cool'n'Quiet na AMD)

Global C-States Control

🕹️ 5. Mouse, Input Lag e Responsividade:
Raw Input / Desativar Acceleração:
👉 Painel de Controle > Mouse > Desmarcar "Aprimorar Precisão".

Polling Rate:
👉 Se o mouse permite: 1000Hz ou mais.

Timer Resolution:
👉 Use o software Timer Resolution
👉 Fixe em 0.5ms (se possível).

ISLC (Intelligent Standby List Cleaner):
👉 Configure pra limpar sempre que o standby cache passar de 1024MB.

📡 6. Rede / Latência / Packet Loss:
Netsh Tweaks:

cmd
Copiar
Editar
netsh interface tcp set global autotuninglevel=disabled
netsh interface tcp set global rss=enabled
netsh interface tcp set global chimney=enabled
Desative Large Send Offload (LSO):

👉 Gerenciador de Dispositivos > Adaptador de Rede > Avançado > LSO v2 IPv4 e IPv6 > Desativar

Interrupt Moderation / Energy-Efficient Ethernet:
👉 Desative ambas.

🧹 7. Limpeza e Compactação de Sistema:
Limpeza de Disco:
👉 Execute cleanmgr /sageset:1 depois cleanmgr /sagerun:1

Remover Restos de Windows Update:
👉 CMD como Admin:

cmd
Copiar
Editar
Dism /Online /Cleanup-Image /StartComponentCleanup /ResetBase
Excluir arquivos de Prefetch e Temp:

cmd
Copiar
Editar
del /f /s /q %SystemRoot%\Prefetch\*
del /q/f/s %TEMP%\*
🔥 8. Windows Services Hardcore Tweak:
👉 Em services.msc, defina como Desativado:

Serviço	Status
Windows Search	Desativado
SysMain (Superfetch)	Desativado
Connected User Experiences and Telemetry	Desativado
Print Spooler (se não usa impressora)	Desativado
Windows Error Reporting	Desativado
Xbox Services	Desativado
Touch Keyboard	Desativado

⚠️ Desative com cuidado, alguns afetam atualizações e rede.

🖥️ 9. Otimizações de Driver de Vídeo:
AMD: Use 23.5.1, 22.5.1 ou a que der melhor 1% low no seu setup.

NVIDIA: Use 537.42, 531.79 ou versões "low latency tested".

👉 No painel da GPU:

Modo de Energia: "Máximo desempenho"

Triple Buffering: Off

VSync: Off

Texture Filtering Quality: High Performance

🎯 10. Extras:
Desative SysMain, Prefetch, Superfetch
👉 Já abordado.

Customizar Pagefile (memória virtual):
👉 Tamanho fixo, cerca de 4096MB a 8192MB se quiser evitar variações.

Desative Virtualização (se não usar máquinas virtuais):
👉 BIOS > VT-d / AMD-V / Hyper-V: Off

✅ Checklist Final Antes de Jogar:
✔️ ISLC rodando
✔️ Timer Resolution ativo
✔️ Processos de fundo mínimos
✔️ Drivers atualizados
✔️ Streaming / Overlay desativados (ex: Discord Overlay, Steam Overlay)
✔️ Config gráfica em modo desempenho extremo
