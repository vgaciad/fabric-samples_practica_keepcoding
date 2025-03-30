Práctica: Hyperledger Fabric Keepcoding

Víctor García Delgado

Entregas:
 1. Readme.md
 2. Doc adjunto: Guía de ejecución de la práctica
 3. Enlace de git: https://github.com/vgaciad/fabric-samples_practica_keepcoding/ con el fork de la red de Hyperledger con los cambios realizados

## 1 Clonamos el repositorio de fabric-samples
Para empezar, vamos hacer un fork del repositorio oficial de Fabric Samples y clonarlo en nuestro entorno de trabajo:
Clonar el repositorio:
git clone https://github.com/hyperledger/fabric-samples.git
cd fabric-samples

## 2 Configuramos la red test-network
La red de prueba por defecto tiene dos organizaciones, pero para este caso de uso debemos agregar una tercera organización.
![image](https://github.com/user-attachments/assets/bf47b34c-b6ac-4561-8bd7-1825368bef41)

2.1 Agregar la organización Distribuidor  

2.2 Generamos los artefactos de configuración

  
## 3 Implementar el chaincode
3.1 Crear un nuevo chaincode
  1. En el directorio chaincode/, creamos  una nueva carpeta para el chaincode.
  2. Escribimos la lógica del contrato inteligente en Go, Node.js o Java.

3.2 Despleganos el chaincode
  ./network.sh deployCC -ccn supplychain -ccp ../chaincode/supplychain -ccl go

## 4 Probamos la red
Ejecutar transacciones prara  en la CLI para registrar productos y cambiar su estado, por ejemplo: 

peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n basic --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" --peerAddresses localhost:11051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org3.example.com/peers/peer0.org3.example.com/tls/ca.crt" -c '{"function":"InitLedger","Args":[]}'

  
