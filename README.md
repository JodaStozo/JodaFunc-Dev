# JodaFunc-Dev
![](http://www.joda.com.br/images/Joda03.png) 

<http://www.joda.com.br>

Desenvolvimento de Funcionalidades para a Plataforma Joda.
Para desenvolver funcionalidades para a Plataforma Joda, o desenvolvedor precisará das seguintes bibliotecas:

## Bibliotecas Básicas
- Argumentos 
  ___(Joda.Argumentos.dll)___
- Tradutor 
  ___(Joda.Tradutor.dll)___
- Mensageiro 
  ___(Joda.Mensageiro.dll)___

Para desenvolvimento mais avançado, o desenvovedor poderá contar com a as seguintes bibliotecas:
## Bibliotecas Adicionais
- Web
  ___(Joda.Web.dll)___
- API
  ___(Joda.API.dll)___
- Pacote
  ___(Joda.Pacote.dll)___

As bibliotecas são desenvolvidas para &reg;Microsoft .NET

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
    'Metodo público acionado pela plataforma ao Iniciar a Funcionalidade
    Public Sub Carregar()
        MeuTradutor.Traduzir(Me)
        If Argumentos.Contar > 0 Then
            Try
                Dim meuInfo As New IO.FileInfo(Argumentos.Valor(1))
                If meuInfo.Exists Then
                    '...
                    Dim mensagemTraduzida As String =
                        MeuTradutor.Traduzir("A Funcionalidade foi carregada com sucesso.")
                    Dim minhaMsg As New Joda.Mensageiro.Mensagem(Joda.Mensageiro.Mensagem.eTipo.Ok,
                                        tituloTraduzido, mensagemTraduzida,
                                        String.Empty)
                    MeuMensageiro.Mostrar(minhaMsg)
                Else
                    MeuMensageiro.Mostrar(New Exception(MeuTradutor.Traduzir("Arquivo {0} não foi localizado", meuInfo.Name)))
                End If
            Catch ex As Exception
                MeuMensageiro.Mostrar(ex)
            End Try
        Else
            MeuMensageiro.Mostrar(New Exception(MeuTradutor.Traduzir("Não foi informado argumento de inicialização")))
        End If
    End Sub
End Class
```
## Exemplos de Uso em C# .NET
### Classe do Objeto principal
```C#
public class ContAloMundo
{
    public Joda.Argumentos.MeusArgumentos Argumentos { get; set; } = new Joda.Argumentos.MeusArgumentos();
    public TabPage minhaTabpage { get; set; }
    public event AoAlterarEventHandler AoAlterar;

    public delegate void AoAlterarEventHandler(object sender, bool argPodeFechar);

    public event FecharEventHandler Fechar;

    public delegate void FecharEventHandler(object sender, bool argPodeFechar);

    public Joda.Tradutor.Tradutor MeuTradutor { get; set; }
    public Joda.Mensageiro.ContMensageiro MeuMensageiro { get; set; }
    // Metodo público acionado pela plataforma ao Iniciar a Funcionalidade
    public void Carregar()
    {
        MeuTradutor.Traduzir(this);
        if (Argumentos.Contar > 0)
        {
            try
            {
                System.IO.FileInfo meuInfo = new System.IO.FileInfo(Argumentos.Valor(1));
                if (meuInfo.Exists)
                {
                }
                else
                    MeuMensageiro.Mostrar(new Exception(MeuTradutor.Traduzir("Arquivo {0} não foi localizado", meuInfo.Name)));
            }
            catch (Exception ex)
            {
                MeuMensageiro.Mostrar(ex);
            }
        }
        else
            MeuMensageiro.Mostrar(new Exception(MeuTradutor.Traduzir("Não foi informado argumento de inicialização")));
    }
}
```
