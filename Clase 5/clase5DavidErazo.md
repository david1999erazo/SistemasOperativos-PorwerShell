# Ejercicios Clase 5 Sistemas Operativos

## David Alejandro Erazo Ochoa
## Código: A00130528

#### 1.¿Cuál clase puede emplearse para consultar la dirección IP de un adaptador de red? ¿Posee dicha clase algún método para liberar un préstamo de dirección (lease) DHCP?

```powershell
    Get-CimInstance win32_networkadapterconfiguration | Select-Object IP
```

#### 2.Despliegue una lista de parches empleando WMI (Microsoft se refiere a los parches con el nombre quick-fix engineering). Es diferente el listado al que produce el cmdlet Get-Hotfix?


```powershell
    Get-WmiObject win32_quickfixengineering
```
##### Existen diferencias en los métodos y propiedades pero el listado es el mismo. 

#### 3.Empleando WMI, muestre una lista de servicios, que incluya su status actual, su modalidad de inicio, y las cuentas que emplean para hacer login.

```powershell
    Get-WmiObject win32_service | Select-Object status, startmode, systemname
```

#### 4. Empleando cmdlets de CIM, liste todas las clases del namespace SecurityCenter2, que tengan product como parte del nombre.

```powershell
    Get-CimClass -Namespace root/SecurityCenter2 | where -Filter {$_.CimClassName -like "*product*"}
```

#### 5. Empleando cmdlets de CIM, y los resultados del ejercicio anterior, muestre los nombres de las aplicaciones antispyware instaladas en el sistema. También puede consultar si hay productos antivirus instalados en el sistema.

##### Antispyware
```powershell
    Get-CimInstance -Namespace root/SecurityCenter2 -ClassName AntiSpywareProduct | Select-Object displayName
```
##### El PC en el cual trabajo no cuenta con aplicaciones antispyware instaladas en el sistema

##### Antivirus
```powershell
    Get-CimInstance -Namespace root/SecurityCenter2 -ClassName AntiVirusProduct | Select-Object displayName
```
