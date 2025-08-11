
O **tcpdump** é uma ferramenta de linha de comando utilizada para capturar e analisar pacotes de dados trafegando em uma rede.  
É essencial para administradores de sistemas, analistas de segurança e profissionais de redes, pois permite inspecionar o tráfego em tempo real ou gravá-lo para análise posterior.

---

## Principais usos

- Capturar pacotes em tempo real para diagnóstico de problemas de rede.  
- Monitorar conexões durante auditorias e testes de segurança.  
- Identificar tráfego suspeito ou anômalo.  
- Filtrar pacotes por IP, porta, protocolo ou direção.  
- Salvar capturas para análise em ferramentas gráficas como **Wireshark**.  

---

## Sintaxe básica

```bash
tcpdump [opções] [expressão]
```

Opções mais comuns:  

-i <interface> → Escolhe a interface de rede (ex.: eth0, wlan0).  

-n → Não converte endereços e portas para nomes.  

-p → Não ativa o modo promíscuo (captura apenas pacotes destinados à interface).  

-v, -vv → Saída detalhada (campos adicionais dos pacotes).  

-w <arquivo> → Salva a captura em arquivo .pcap.  

-r <arquivo> → Lê pacotes de um arquivo .pcap.  

---

## Expressões

Existem três principais expressões do TCPDUMP: type, dir e proto.

As opções do type são:  
- **host**: indicação do host a ser identificado na captura.    
- **net**: indicação da rede a ser identificada na captura.  
- **port**: indicação da porta de comunicação.  

As opções do dir são:  
- **src**: host de origem.  
- **dst**: host de destino.  
- **src or dst**: origem ou destino.  
- **src and dst**: origem e destino.  

A expressão proto permite a seleção dos protocolos: tcp, udp, icmp, entre outras opções tratadas pelo tcpdump.



---

## Exemplos de uso

Capturar pacotes de uma interface específica
```bash
sudo tcpdump -i eth0
```
Capturar pacotes sem resolução de nomes
```bash
sudo tcpdump -i eth0 -n
```
Capturar tráfego ICMP (ping)
```bash
sudo tcpdump -i eth0 icmp
```
Capturar tráfego para a porta 80 (HTTP)
```bash
sudo tcpdump -i eth0 port 80
```
Capturar tráfego de um host específico
```bash
sudo tcpdump -i eth0 host 192.168.0.10
```
Salvar captura em arquivo
```bash
sudo tcpdump -i eth0 -w captura.pcap
```
Ler captura salva
```bash
tcpdump -r captura.pcap
```

---

## Interpretando a saída

Exemplo:
```bash
22:01:07.710000 192.168.0.2.1173 > 192.168.0.30.21: S 32691180:32691180(0) win 512
```

- 22:01:07.710000 → Horário da captura (HH:MM:SS.microsegundos).  

- 192.168.0.2 → IP de origem.  

- 1173 → Porta de origem.  

- ">" → Direção do tráfego.  

- 192.168.0.30 → IP de destino.  

- 21 → Porta de destino.  

- S → Flag TCP SYN (início de conexão).  

- 32691180:32691180(0) → Números de sequência inicial/final e quantidade de bytes.  

- win 512 → Tamanho da janela de recepção.  

!!! tip "Dicas de uso"
    Filtrar pacotes por protrocolo:
    ```bash
    tcpdump -i eth0 tcp
    ```
    Filtrar pacotes destinados a uma rede inteira:
    ```bash
    tcpdump -i eth0 net 192.168.0.0/24
    ```
    Filtrar pacotes com origem ou destino específicos:
    ```bash
    tcpdump -i eth0 src host 192.168.0.10
    tcpdump -i eth0 dst port 443
    ```
    Monitorar em tempo real com nível de detalhe:
    ```bash
    sudo tcpdump -i eth0 -n -vv
    ```

!!! warning "Atenção"
    O tcpdump pode capturar dados sensíveis. Use somente em redes autorizadas.

    Para capturar todos os pacotes possíveis, é necessário executá-lo com privilégios de administrador (sudo).

    Capturas longas podem gerar arquivos muito grandes.

---

## Referências

- Comando  
```bash
man tcpdump
```
- [Documentação oficial do tcpdump](https://www.tcpdump.org/)  
- [Guia de filtros BPF - tcpdump](https://biot.com/capstats/bpf.html)  
- [Wireshark - Analisando arquivos .pcap](https://www.wireshark.org/)