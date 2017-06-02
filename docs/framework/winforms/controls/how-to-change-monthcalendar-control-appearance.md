---
title: "Comment&#160;: modifier l&#39;apparence du contr&#244;le MonthCalendar Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "exemples (Windows Forms), contrôles calendar"
  - "MonthBackColor (propriété)"
  - "MonthCalendar (contrôle Windows Forms), mettre en forme l'affichage"
  - "TitleBackColor (propriété)"
  - "TitleForeColor (propriété)"
  - "TrailingForeColor (propriété)"
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: modifier l&#39;apparence du contr&#244;le MonthCalendar Windows Forms
Le contrôle <xref:System.Windows.Forms.MonthCalendar> Windows Forms vous permet de personnaliser l'apparence du calendrier de nombreuses façons.  Vous pouvez, par exemple, modifier son modèle de couleurs et choisir d'afficher ou de masquer les numéros des semaines et la date actuelle.  
  
### Pour modifier le modèle de couleurs du calendrier mensuel  
  
-   Définissez des propriétés telles que <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> et <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.  La propriété <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> détermine également la couleur de la police des jours de la semaine.  La propriété <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> détermine la couleur des dates qui précèdent et suivent le mois ou les mois affichés.  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    >  Démarrer avec Windows Vista et en fonction du thème, la définition de certaines propriétés ne modifiera pas nécessairement l'aspect du calendrier.  Par exemple, si Windows est définie pour utiliser le thème Aero, la définition des propriétés <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> ou <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> n'a aucun effet.  En fait, une version mise à jour du calendrier est affichée avec un aspect dérivé au moment de l'exécution du thème issu du système d'exploitation actuel.  Si vous souhaitez utiliser ces propriétés et activer la version antérieure du calendrier, vous pouvez désactiver les styles visuels de votre application.  La désactivation des styles visuels peut affecter l'aspect et le comportement d'autres contrôles dans votre application.  Pour désactiver les styles visuels en Visual Basic, ouvrez le Concepteur de projets et désactivez la case à cocher **Activer les styles visuels XP**.  Pour désactiver les styles visuels dans C\#, ouvrez Program.cs et supprimez le commentaire `Application.EnableVisualStyles();`.  Pour plus d'informations sur les styles visuels, consultez [How to: Enable Windows XP Visual Styles](http://msdn.microsoft.com/fr-fr/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).  
  
### Pour afficher la date actuelle en bas du contrôle  
  
-   Affectez à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> la valeur `true`.  L'exemple suivant bascule entre l'affichage et le masquage de la date du jour lorsque vous double\-cliquez sur le formulaire.  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### Pour afficher les numéros de semaine  
  
-   Affectez à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> la valeur `true`.  Vous pouvez définir cette propriété dans le code ou dans la fenêtre Propriétés.  
  
     Les numéros de semaine apparaissent dans une colonne distincte, à gauche du premier jour de la semaine.  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## Voir aussi  
 [MonthCalendar, contrôle](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [Comment : sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)   
 [Comment : afficher en gras certains jours à l'aide du contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)   
 [Comment : afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)