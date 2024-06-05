import yfinance


ticker = input("Digite o codigo da ação desejada:")

dados= yfinance.Ticker(ticker).history(start="2020-01-01", end="2020-12-31")
fechamento = dados.Close
fechamento.plot()



maxima = round(fechamento.max(), 2)
minima = round(fechamento.min(), 2)
valor_medio = round(fechamento.mean(), 2)

print(maxima)
print(minima)
print(valor_medio)


from datetime import time
import pyautogui
import pyperclip
import webbrowser
import time

destinatario =  "allansiqueira06@gmail.com"
assunto = "Analise do projeto"

mensagem = f"""
Segue as informações da ação {ticker}

Cotação maxima:{maxima}
Cotação minima:{minima}
Valor medio:{valor_medio}
"""

webbrowser.open("www.gmail.com")
time.sleep(5)


pyautogui.PAUSE = 5


pyautogui.click(x=80, y=210)

pyperclip.copy(destinatario)
pyautogui.hotkey("ctrl", "v")
pyautogui.hotkey("tab")

pyperclip.copy(assunto)
pyautogui.hotkey("ctrl", "v")
pyautogui.hotkey("tab")

pyperclip.copy(mensagem)
pyautogui.hotkey("ctrl", "v")

pyautogui.click(x=826, y=684)

print("Email enviado com sucesso")
