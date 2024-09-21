<- [Previus](welcome_doc.md)

# SapGui


1. [Parameters](#parameters)
2. [Methods](#methods-sapgui)

```python
SapGui(
    path_logon:str = r"C:\Program Files (x86)\SAP\FrontEnd\SAPgui\saplogon.exe",
    rest_time: float = 0.5,
    conection:Literal = "PRODUCTIVO",
    user: str  = "",
    password: str = "",
    client: str = "400",
    lenguage: Literal= "ES",
    option_multiple_logons:Literal = "2",
    active: bool = False
)
```

## Parameters: 
- path_logon: The file path to the SAP Logon executable. Defaults to the standard installation path.
- rest_time: The delay time (in seconds) between steps in the logon process. Default is 0.5 seconds.
- conection: The type of SAP connection to use.Default is "PRODUCTIVO".
- user: The SAP username. Default is an empty string.
- password: The SAP password. Default is an empty string.
- client: The SAP client number. Default is "400".
- lenguage: The language for the SAP session.  
    - "EN" for English,
    - "ES" for Spanish.
    - Default is "ES".
- option_multiple_logons: The action to take if multiple logons are detected 
    - "1" - Continue with this logon and end any other logons in the system. 
    - "2" - Continue with this logon, without ending any other logons in the system.
    - "3" - Terminate this logon 
    - Default is "2",
- active: Select the SAP logon detected

## Examples

> * If you don't know your sap connection you can find it in the SAP Logon window.
<img title="Ubication conections" src="https://help.sap.com/doc/63bd20104af84112973ad59590645513/800.08/en-US/loiofbe475977b184e3aba5d80315d83adf0_LowRes.png">
in this case it has 4 available connections: CSS[PUBLIC] - EBS[PUBLIC] - I7P[PUBLIC] - ISP[PUBLIC]

- ### Basic usage
    
    ```python
    sap_instance=SapGui(
        conection = "YOUR CONECTION",
        user = "User",
        password = "Password",
    )
    ```
- ### Active SAP
    
    ```python
    sap_instance=SapGui(
        active=True
    )
    ```
- ### Custom init
    
    ```python
    sap_instance=SapGui(
        path_logon = r"your_address\saplogon.exe",
        rest_time = 0.8,
        conection = "EBS[PUBLIC]",
        user = "USUARIO",
        password = "PASSWORD",
        client = "400",
        lenguage = "ES",
        option_multiple_logons = "1",
    )
    ```

## Methods SapGui(...)

- get_session(self): return GuiSession Object

- get_connection(self): return GuiConnection Object

- close_sap(self): end sap windows

- get_user(self): get the name of sap user

if you want know more about of **GuiObjects**, Explore [Sap Gui Objects](https://help.sap.com/docs/sap_gui_for_windows/b47d018c3b9b45e897faf66a6c0885a8/a2e9357389334dc89eecc1fb13999ee3.html).
