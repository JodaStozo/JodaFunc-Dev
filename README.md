# JodaFunc-Dev
![](http://www.joda.com.br/images/Joda03.png) 

: <http://www.joda.com.br>

Desenvolvimento de Funcionalidades para a Plataforma Joda.
Para desenvolver funcionalidades para a Plataforma Joda, o desenvolvedor precisará das seguintes bibliotecas:

## Bibliotecas Básicas
- Argumentos 
  ___(Joda.Argumentos.dll)___
- Tradutor 
  ___(Joda.Tradutor.dll)___
- Mensageiro 
  ___(Joda.Mensageiro.dll)___

As bibliotecas são desenvolvidas para Microsoft .NET

Para desenvolvimento mais avançado, o desenvovedor poderá contar com a as seguintes bibliotecas:
## Bibliotecas Adicionais
- Web
  ___(Joda.Web.dll)___
- API
  ___(Joda.API.dll)___
- Pacote
  ___(Joda.Pacote.dll)___

## Exemplos de Uso em VB .NET
### Classe do Objeto principal
O objeto principal deve ser do tipo "Controle de Usuário" em um projeto do tipo "Biblioteca de Classe" (.dll)

```VB
Public Class ContAloMundo
    Public Property Argumentos As New Joda.Argumentos.MeusArgumentos
    Public Property minhaTabpage As TabPage
    Public Event AoAlterar(ByVal sender As Object, ByVal argPodeFechar As Boolean)
    Public Event Fechar(ByVal sender As Object, ByVal argPodeFechar As Boolean)
    Public Property MeuTradutor As Joda.Tradutor.Tradutor
    Public Property MeuMensageiro As Joda.Mensageiro.ContMensageiro

    Public Sub Carregar()

    End Sub

End Class
```
