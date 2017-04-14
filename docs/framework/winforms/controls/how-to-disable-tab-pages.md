---
title: "Comment&#160;: d&#233;sactiver les pages d&#39;onglets | Microsoft Docs"
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
  - "pages d'onglets, masquer dans les formulaires"
  - "TabControl (contrôle Windows Forms), désactiver les pages"
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: d&#233;sactiver les pages d&#39;onglets
Dans certains cas, vous souhaiterez limiter l'accès aux données disponibles dans votre application Windows Forms.  Par exemple, si des données sont affichées dans les pages d'onglets d'un contrôle Tab, il se peut que vous souhaitiez autoriser les administrateurs à accéder aux informations d'une page d'onglets, mais pas les utilisateurs invités ou de niveau inférieur.  
  
### Pour désactiver des pages d'onglets par programmation  
  
1.  Écrivez le code permettant de gérer l'événement <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> du contrôle Tab.  Il s'agit de l'événement généré lorsque l'utilisateur bascule d'un onglet à l'autre.  
  
2.  Vérifiez les informations d'identification.  En fonction des informations présentées, vous pouvez vérifier le nom d'utilisateur sous lequel l'utilisateur a ouvert une session, ou toute autre forme d'information d'identification autorisant l'utilisateur à afficher l'onglet.  
  
3.  Si l'utilisateur dispose d'informations d'identification appropriées, affichez l'onglet sur lequel il a cliqué.  Sinon, affichez une boîte de message ou tout autre élément d'interface utilisateur indiquant que l'utilisateur ne dispose pas des privilèges d'accès requis, et retournez à l'onglet initial.  
  
    > [!NOTE]
    >  Lorsque vous implémentez cette fonctionnalité dans vos applications de production, vous pouvez effectuer cette vérification des informations d'identification au cours de l'événement <xref:System.Windows.Forms.Form.Load> du formulaire.  Cela vous permet de masquer l'onglet avant l'affichage de tout élément d'interface utilisateur, ce qui constitue une approche beaucoup plus soignée de la programmation.  La méthodologie ci\-après \(vérification des informations d'identification et désactivation de l'onglet au cours de l'événement <xref:System.Windows.Forms.TabControl.SelectedIndexChanged>\) est utilisée à des fins d'illustration.  
  
4.  Si vous avez plus de deux pages d'onglets, vous pouvez également afficher une page différemment de l'original.  
  
     Dans l'exemple ci\-dessous, un contrôle <xref:System.Windows.Forms.CheckBox> est utilisé à la place de la vérification des informations d'identification, dans la mesure où les critères d'accès à l'onglet dépendent de l'application.  Lorsque l'événement <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> est généré, si la vérification des informations d'identification est vraie \(c'est\-à\-dire si la case à cocher est activée\) et que l'onglet sélectionné est `TabPage2` \(celui qui comporte les informations confidentielles, dans cet exemple\), l'onglet `TabPage2` s'affiche.  Dans le cas contraire, `TabPage3` s'affiche et une zone de message est présentée à l'utilisateur, indiquant qu'il ne disposait pas des privilèges d'accès appropriés.  Le code ci\-dessous illustre un formulaire avec un contrôle <xref:System.Windows.Forms.CheckBox> \(`CredentialCheck`\) et un contrôle <xref:System.Windows.Forms.TabControl> comportant trois pages d'onglets.  
  
    ```vb  
    Private Sub TabControl1_SelectedIndexChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles TabControl1.SelectedIndexChanged  
       ' Check Credentials Here  
  
       If CredentialCheck.Checked = True And _   
       TabControl1.SelectedTab Is TabPage2 Then  
          TabControl1.SelectedTab = TabPage2  
       ElseIf CredentialCheck.Checked = False _   
       And TabControl1.SelectedTab Is TabPage2 Then  
          MessageBox.Show _   
         ("Unable to load tab. You have insufficient access privileges.")  
          TabControl1.SelectedTab = TabPage3  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void tabControl1_SelectedIndexChanged(object sender, System.EventArgs e)  
    {  
        // Check Credentials Here  
  
        if ((CredentialCheck.Checked == true) && (tabControl1.SelectedTab == tabPage2))   
        {  
            tabControl1.SelectedTab = tabPage2;  
        }  
        else if ((CredentialCheck.Checked == false) && (tabControl1.SelectedTab == tabPage2))  
        {  
            MessageBox.Show("Unable to load tab. You have insufficient access privileges.");  
            tabControl1.SelectedTab = tabPage3;  
        }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       System::Void tabControl1_SelectedIndexChanged(  
          System::Object ^ sender,  
          System::EventArgs ^  e)  
       {  
          // Check Credentials Here  
          if ((CredentialCheck->Checked == true) &&  
              (tabControl1->SelectedTab == tabPage2))  
          {  
             tabControl1->SelectedTab = tabPage2;  
          }  
          else if ((CredentialCheck->Checked == false) &&  
                   (tabControl1->SelectedTab == tabPage2))  
          {  
             MessageBox::Show(String::Concat("Unable to load tab. ",  
                "You have insufficient access privileges."));  
             tabControl1->SelectedTab = tabPage3;  
          }  
       }  
    ```  
  
     \(Visual C\#, Visual C\+\+\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## Voir aussi  
 [Vue d'ensemble du contrôle TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [Comment : ajouter un contrôle à une page d'onglet](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)   
 [Comment : ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)   
 [Comment : modifier l'apparence du contrôle TabControl Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)