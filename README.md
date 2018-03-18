# python-OP_RETURN
Modificación de la librería diseñada por [coinsecrets.org](http://coinsecrets.org/), que permite la utilización del OP_RETURN en las transacciones de [Chaucha](https://chaucha.cl).

## Requerimientos

* Python 2.5 o superior (incluido Python 3.x)
* [Chauchera](https://github.com/proyecto-chaucha/chauchera) versión 2.1.0.0

Antes de utilizar se recomienda revisar la configuración en el archivo OP_RETURN.py (variable OP_RETURN_BITCOIN_USE_CMD), a modo de configurar la comunicación directa usando chaucha-cli o la comunicación RPC.

## Modo de uso

### Linea de comandos

#### Sintaxis de uso:
``python send-OP_RETURN.py <dirección> <monto> <mensaje> <testnet (optional)>``

* **<dirección>**: Salida de la transacción a realizar, dirección que mantendrá el registro de mensajes a enviar
* **<monto>**: Cantidad de Chauchas a enviar (recomendado: 0.001)
* **<mensaje>**: Información a escribir en el Blockchain (Max 256 bytes)
* **<testnet>**: Utilizar la red de pruebas (testnet) para enviar la transacción

#### Ejemplos

Mainnet:
``python send-OP_RETURN.py 149wHUMa41Xm2jnZtqgRx94uGbZD9kPXnS 0.001 'Hello, blockchain!'``

Testnet:
``python send-OP_RETURN.py mzEJxCrdva57shpv62udriBBgMECmaPce4 0.001 'Hello, testnet!' 1``

#### Librería en Python

Código de ejemplo:

```python
from OP_RETURN import *

def main():
    address = 'cWjzyUJaAGzCMj7FpvSovG5r9HeFafz1E3'
    monto = 1.0
    msg = 'waiworinao'
    tesnet = False
    
    resultado = OP_RETURN_send(address, monto, msg, testnet)
    if 'error' in resultado:
	    print('Error: ' + result['error'])
    else:
	    print('TxID: ' + result['txid'])

if __name__ == '__main__':
	main()
```