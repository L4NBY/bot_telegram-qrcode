# bot telegram gerrar qrcode 

Comandos

/qr ou /qrcode 

Dependências 🤪
```
pip install qrcode
```
# emxeplo 

```
/qr ola tudo bem ? 
```

# Código 

```

@bot.message_handler(commands=['qr' , 'qrcode'])
def email_0(mensagem):
    if mensagem.text == '/qr':
        bot.send_message(mensagem.chat.id , f'O **{mensagem.from_user.first_name }** , NÃO É ASSIM EXEMPLO ``` /qr ola tudo bem ```  **ou** ``` /qrcode ola tudo bem ``` ' , parse_mode='Markdown')
        return  False
    elif mensagem.text == '/qrcode':
        bot.send_message(mensagem.chat.id , f'O **{mensagem.from_user.first_name }** , NÃO É ASSIM EXEMPLO ``` /qr ola tudo bem ```  **ou** ``` /qrcode ola tudo bem ``` ' , parse_mode='Markdown')
        return  False
        
    try:
        ot = mensagem.text.lstrip('/qr').lstrip('/qrcode').lstrip()
        print(ot)
        
        qr = qrcode.QRCode(None , qrcode.ERROR_CORRECT_H)
        qr.add_data(ot)
        IMG = qr.make_image(fill_color='green' ,                     back_color='black')
        IMG.save('bot_lanby_qrcode.jpg')
        foto_ = open('bot_lanby_qrcode.jpg', 'rb')
        bot.send_photo(mensagem.chat.id , foto_)
        
    except:
        bot.send_message(mensagem.chat.id , f'NAO FOI POSSÍVEL GERRAR O SEU QRCODE @{mensagem.from_user.first_name}')
```
