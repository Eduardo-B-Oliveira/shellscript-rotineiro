#!/bin/bash

echo "Digite o diretório de origem:"
read origem

echo "Digite o diretório de destino:"
read destino

echo "Digite a frequência de backup em segundos:"
read frequencia

# Verificar se os diretórios existem
if [ ! -d "$origem" ]; then
    echo "Diretório de origem não existe."
    exit 1
fi

if [ ! -d "$destino" ]; then
    echo "Diretório de destino não existe. Deseja criar? (s/n)"
    read criar
    if [ "$criar" = "s" ]; then
        mkdir -p "$destino"
    else
        echo "Backup cancelado."
        exit 1
    fi
fi

while true; do
    echo "Iniciando backup..."

    # Copiar arquivos do diretório de origem para o diretório de destino
    for arquivo in "$origem"/*; do
        if [ -f "$arquivo" ]; then
            cp "$arquivo" "$destino"
        fi
    done

    echo "Backup concluído. Aguardando $frequencia segundos para o próximo backup..."

    sleep "$frequencia"

    echo "Deseja continuar o backup? (s/n)"
    read continuar
    case "$continuar" in
s|S)
            echo "Continuando o backup..."
            ;;
        n|N)
            echo "Backup interrompido pelo usuário."
            break
            ;;
        *)
            echo "Opção inválida. Backup interrompido."
            break
            ;;
    esac
done
