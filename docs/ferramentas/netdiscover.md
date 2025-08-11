# Netdiscover

O **netdiscover** é uma ferramenta de linha de comando utilizada para descoberta de hosts ativos em uma rede local, 
realizando varreduras através de requisições **ARP**.  
Ele é muito útil em redes sem servidor DHCP ou para mapear dispositivos rapidamente.

---

## Principais usos

- Identificar dispositivos conectados na rede local.
- Descobrir IPs e endereços MAC ativos.
- Mapear redes desconhecidas.
- Realizar auditorias de segurança para verificar hosts ativos.

---

## Sintaxe básica

```bash
netdiscover [opções]
```

---

## Opções comuns

- `-i <interface>` → Define a interface de rede.
- `-r <range>` → Define o intervalo de IPs a serem escaneados.
- `-p` → Modo passivo (escuta apenas, sem enviar pacotes ARP).
- `-s <tempo>` → Define o tempo de espera entre pacotes enviados.

---

## Exemplos de uso

### Escanear uma sub-rede inteira
```bash
sudo netdiscover -r 192.168.0.0/24
```

### Usar interface específica
```bash
sudo netdiscover -i eth0 -r 10.0.0.0/24
```

### Modo passivo (sem enviar pacotes)
```bash
sudo netdiscover -p
```

---

##  Observações

- É necessário executar como **root** para acesso total à interface de rede.
- Em modo ativo, o `netdiscover` envia pacotes ARP para todo o intervalo especificado.
- Em modo passivo, ele apenas monitora requisições/respostas ARP já existentes.

---

##  Referências

- `man netdiscover`
- [Página oficial do projeto](https://github.com/alexxy/netdiscover)
