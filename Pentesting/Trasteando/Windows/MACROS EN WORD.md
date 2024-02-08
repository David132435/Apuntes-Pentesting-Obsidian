----
- tags: #macros #word #excel #microsoft #office #troyano #windows #powerpoint #rce 
---

> En un documento Word vamos a **Vista**, después a **Macros** **Ver Macros**.

![[Pasted image 20240204183006.png|800]]

> Le pondremos de nombre **AutoExec**, **seleccionaremos el documento actual** y haremos clic en **Crear**

![[Pasted image 20240204183345.png]]

> Ponemos nuestro código sacado de esta página donde usan HoaxShell para bypassear Defender (https://infayer.com/archivos/1917) y luego crean una macro en Word con ello.

```
Sub AutoOpen()

    Dim Shell As Object
    Set Shell = CreateObject("wscript.shell")
    Shell.Run "calc.exe"

End Sub
```


![[Pasted image 20240204183538.png|800]]







