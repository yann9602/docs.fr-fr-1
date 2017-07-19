---
title: "Polices internationales pour les applications Windows Forms et les contr&#244;les | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "police de substitution dans les Windows Forms"
  - "polices, considérations relatives à la globalisation"
  - "polices, international"
  - "globalisation (Windows Forms), jeux de caractères"
  - "applications internationales (Windows Forms), affichage des caractères"
  - "localisation (Windows Forms), polices"
  - "contrôles Windows Forms, étiquettes"
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Polices internationales pour les applications Windows Forms et les contr&#244;les
Dans les applications internationales, la méthode de sélection des polices recommandée est l'utilisation de la police de substitution autant que possible.  Police de substitution signifie que le système détermine le script auquel appartient le caractère.  
  
## Utilisation de la police de secours  
 Pour bénéficier de cette fonctionnalité, ne définissez pas la propriété <xref:System.Drawing.Font> pour votre formulaire ou tout autre élément.  L'application utilisera automatiquement la police système par défaut, qui diffère d'une langue localisée du système d'exploitation à une autre.  Lorsque l'application s'exécute, le système fournit automatiquement la police adaptée à la culture sélectionnée dans le système d'exploitation.  
  
 La modification du style de police constitue une exception à la règle de non\-paramétrage de la police.  Ceci peut être important pour une application dans laquelle l'utilisateur clique sur un bouton pour faire apparaître le texte en gras dans une zone de texte.  Pour ce faire, vous devez écrire une fonction qui convertit le style de police de la zone de texte en gras, indépendamment de la police du formulaire.  Il est important d'appeler cette fonction à deux endroits : dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> et le gestionnaire d'événements <xref:System.Windows.Forms.Control.FontChanged> du bouton.  Si la fonction est uniquement appelée dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> et qu'un autre fragment du code modifie la famille de polices de l'ensemble du formulaire, la zone de texte ne changera pas avec le reste du formulaire.  
  
```  
' Visual Basic  
Private Sub MakeBold()  
   ' Change the TextBox to a bold version of the form font  
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
   ' Clicking this button makes the TextBox bold  
   MakeBold()  
End Sub  
  
Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged  
   ' If the TextBox is already bold and the form's font changes,  
   ' change the TextBox to a bold version of the new form font  
   If (TextBox1.Font.Style = FontStyle.Bold) Then  
      MakeBold()  
   End If  
End Sub  
  
// C#  
private void button1_Click(object sender, System.EventArgs e)  
{  
   // Clicking this button makes the TextBox bold  
   MakeBold();  
}  
  
private void MakeBold()   
{  
   // Change the TextBox to a bold version of the form's font  
   textBox1.Font = new Font(this.Font, FontStyle.Bold);  
}  
  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
   // If the TextBox is already bold and the form's font changes,  
   // change the TextBox to a bold version of the new form font  
   if (textBox1.Font.Style == FontStyle.Bold)   
   {  
      MakeBold();  
   }  
}  
```  
  
 Toutefois, lorsque vous localisez votre application, la police grasse peut s'afficher de façon incorrecte pour certaines langues.  Si ce problème se pose, il sera utile aux localisateurs de pouvoir basculer la police de gras en texte normal.  En règle générale, les localisateurs ne sont pas des développeurs et n'ont pas accès au code source mais uniquement aux fichiers de ressources. Cette option doit donc être définie dans les fichiers de ressources.  Pour ce faire, attribuez la valeur `true` à la propriété <xref:System.Drawing.Font.Bold%2A>.  La configuration de la police est alors écrite dans les fichiers de ressources. Les localisateurs peuvent donc la modifier.  Écrivez ensuite le code après la méthode `InitializeComponent`  pour rétablir la police quelle que soit la police du formulaire, en utilisant le style de police spécifié dans le fichier de ressources.  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## Voir aussi  
 [Globalisation des Windows Forms](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)   
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)