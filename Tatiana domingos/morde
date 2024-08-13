import os
import sys
import datetime
import pandas as pd
from config import file_path, dict_morse

def decode_morse(msg):
    '''
    input : mensagem em código morse com as letras separadas por espaços
    output : palavra escrito em letras e algarismos
    '''
    palavras = msg.split('  ')
    frase_decifrada = []

    for palavra in palavras:
        # Separar as letras por um espaço
        msg_list = palavra.split(' ')
        palavra_decifrada = ''.join([dict_morse.get(letter, '') for letter in msg_list])
        frase_decifrada.append(palavra_decifrada)

    return ' '.join(frase_decifrada)

def save_clear_msg_csv_hdr(msg_claro):
    '''
    input : mensagem em texto claro
    output : palavra escrito em letras e algarismos, salva em arquivo csv
    '''
    now = datetime.datetime.now()
    df = pd.DataFrame([[msg_claro, now]], columns=["mensagem", "datetime"])
    hdr = not os.path.exists(file_path)
    df.to_csv(file_path, mode ="a", index = False, header=hdr)


if __name__ == "__main__":
    msg_claro = decode_morse(sys.argv[1])
    save_clear_msg_csv_hdr(msg_claro)
