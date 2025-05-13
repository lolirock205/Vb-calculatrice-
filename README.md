Public Class Form1

    Dim operation As String = ""
    Dim result As Double = 0
    Dim newOperation As Boolean = False

    Private Sub AjouterValeur(sender As Object, e As EventArgs) Handles _
        Button0.Click, Button1.Click, Button2.Click, Button3.Click, Button4.Click, _
        Button5.Click, Button6.Click, Button7.Click, Button8.Click, Button9.Click, ButtonDot.Click

        Dim btn As Button = CType(sender, Button)

        If newOperation Or TextBox1.Text = "0" Then
            TextBox1.Text = ""
            newOperation = False
        End If

        TextBox1.Text &= btn.Text
    End Sub

    Private Sub Operation_Click(sender As Object, e As EventArgs) Handles _
        ButtonAdd.Click, ButtonSub.Click, ButtonMul.Click, ButtonDiv.Click

        Dim btn As Button = CType(sender, Button)

        Try
            result = CDbl(TextBox1.Text)
            operation = btn.Text
            newOperation = True
        Catch ex As Exception
            TextBox1.Text = "Erreur"
        End Try
    End Sub

    Private Sub ButtonEqual_Click(sender As Object, e As EventArgs) Handles ButtonEqual.Click
        Try
            Dim secondValue As Double = CDbl(TextBox1.Text)

            Select Case operation
                Case "+"
                    result += secondValue
                Case "-"
                    result -= secondValue
                Case "*"
                    result *= secondValue
                Case "/"
                    If secondValue = 0 Then
                        TextBox1.Text = "Division par 0"
                        Exit Sub
                    End If
                    result /= secondValue
            End Select

            TextBox1.Text = result.ToString()
            newOperation = True

        Catch ex As Exception
            TextBox1.Text = "Erreur"
        End Try
    End Sub

    Private Sub ButtonClear_Click(sender As Object, e As EventArgs) Handles ButtonClear.Click
        TextBox1.Text = "0"
        result = 0
        operation = ""
    End Sub

End Class
