# Ferramentas de Diagnóstico de Rede

Este documento reúne algumas ferramentas fundamentais para testes e diagnósticos de rede: **ping**, **traceroute**, **fping** e **arping**.

---

## ping

O **ping** é uma ferramenta de linha de comando usada para testar a conectividade entre dois dispositivos na rede.  
Ele envia pacotes **ICMP Echo Request** para um destino e aguarda uma resposta **ICMP Echo Reply**.

### Principais usos
- Verificar se um host está acessível.
- Medir tempo de resposta (latência).
- Testar estabilidade da conexão.
- Diagnosticar perdas de pacotes.

### Opções comuns
- `-c <n>` → Envia um número específico de pacotes.
- `-i <seg>` → Intervalo entre pacotes.
- `-s <bytes>` → Tamanho do pacote enviado.
- `-t <ttl>` → Define o valor do TTL (Time-To-Live).

### Exemplos
```bash
# Testar conectividade com 4 pacotes
ping -c 4 google.com

# Definir tamanho do pacote e intervalo
ping -s 1024 -i 0.5 8.8.8.8
```

---

## Traceroute

O **traceroute** mostra o caminho que os pacotes percorrem até o destino, revelando cada roteador intermediário e o tempo até cada salto.

### Principais usos
- Diagnosticar onde a conexão está falhando ou está lenta.
- Visualizar o trajeto dos pacotes até o destino.
- Entender o número de saltos até um host.

### Opções comuns
- `-n` → Não resolve nomes de host (mostra IPs).
- `-w <seg>` → Tempo máximo de espera por resposta.
- `-m <ttl>` → Define o TTL máximo (limite de saltos).

### Exemplos
```bash
# Mostrar caminho até um host
traceroute google.com

# Mostrar caminho usando apenas IPs
traceroute -n 8.8.8.8
```

---

## fping

O **fping** é uma versão avançada do ping, capaz de testar múltiplos hosts de forma simultânea.

### Principais usos
- Verificar status de vários hosts em uma rede.
- Fazer varreduras rápidas para identificar dispositivos ativos.

### Opções comuns
- `-a` → Mostra apenas hosts que responderam.
- `-u` → Mostra apenas hosts que não responderam.
- `-g` → Gera uma lista de IPs em um intervalo.

### Exemplos
```bash
# Testar múltiplos hosts
fping 192.168.0.1 192.168.0.10 192.168.0.20

# Verificar toda a sub-rede
fping -a -g 192.168.0.0/24
```

---

## arping

O **arping** envia pacotes **ARP Request** para descobrir dispositivos na mesma rede local.

### Principais usos
- Descobrir hosts ativos em uma LAN.
- Diagnosticar problemas de resolução ARP.
- Verificar se um endereço IP está em uso.

### Opções comuns
- `-I <interface>` → Define a interface de rede.
- `-c <n>` → Número de pacotes a enviar.

### Exemplos
```bash
# Enviar ARP Requests para um IP
arping 192.168.0.1

# Usar interface específica e limitar número de pacotes
arping -I eth0 -c 5 192.168.0.1
```

---

## Referências

- `man ping`
- `man traceroute`
- `man fping`
- `man arping`
