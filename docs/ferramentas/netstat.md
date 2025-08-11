## **Reconhecendo o alvo com o Netstat**

O **netstat** (*network statistics*) é uma ferramenta de linha de comando utilizada para exibir informações sobre conexões de rede, tabelas de roteamento e estatísticas de interface.  
É amplamente usada para monitorar a atividade de rede, diagnosticar problemas de conectividade e detectar conexões suspeitas.

---

## Principais usos

- Listar conexões TCP e UDP ativas.
- Verificar quais portas estão em escuta (*listening*).
- Identificar o PID e o nome do processo associado a cada conexão.
- Visualizar a tabela de roteamento.
- Monitorar estatísticas de protocolos de rede.

---

## Sintaxe básica

```bash
netstat [opções]
```

-a → Mostra todas as conexões e portas em escuta.

-t → Mostra apenas conexões TCP.

-u → Mostra apenas conexões UDP.

-n → Exibe endereços e portas no formato numérico (não resolve nomes).

-p → Mostra o PID e o nome do processo associado a cada conexão.

-r → Exibe a tabela de roteamento.

-s → Mostra estatísticas por protocolo.

---

## Exemplos de uso

Mostrar todas as conexões TCP  

```bash
netstat -at
```

Mostrar conexões TCP e UDP em formato numérico  

```bash
netstat -atun
```

Listar conexões com PID e nome do processo

```bash
sudo netstat -tulpn
```

Exibir tabela de roteamento

```bash
netstat -r
```

Estatísticas de protocolos

```bash
netstat -s
```

!!! tip "Dica"
    Filtrar resultados por porta:  
    ```bash
    sudo netstat -tulpn | grep 80
    ```
    Monitorar conexões em tempo real:
    ```bash
    watch -n 2 'netstat -atnp'
    ```

---

## Observação sobre sistemas modernos

Em distribuições Linux mais recentes, o netstat foi substituído pelo comando ss, que oferece funcionalidades similares com melhor desempenho.

Exemplo equivalente:  

```bash
ss -atnp
```

---

## Referências
- Comando  
```bash
man netstat
```
- [Documentação do netstat no Linux](https://linux.die.net/man/8/netstat)

