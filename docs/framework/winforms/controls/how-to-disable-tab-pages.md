---
title: "Comment : désactiver les pages d'onglets"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20674a93459f42a793ddf5f7ee5dffb1fa122d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="b369e-102">Comment : désactiver les pages d'onglets</span><span class="sxs-lookup"><span data-stu-id="b369e-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="b369e-103">Dans certains cas, vous devez restreindre l’accès aux données qui sont disponibles dans votre application Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b369e-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="b369e-104">Un exemple peut être lorsque vous avez des données affichées dans les pages d’un contrôle onglet. les administrateurs peut avoir plus d’informations sur une page d’onglet que vous ne souhaitez pas empêcher les invités ou les utilisateurs de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="b369e-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="b369e-105">Pour désactiver les pages d’onglets par programmation</span><span class="sxs-lookup"><span data-stu-id="b369e-105">To disable tab pages programmatically</span></span>  
  
1.  <span data-ttu-id="b369e-106">Écrire du code pour gérer le contrôle d’onglet <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> événement.</span><span class="sxs-lookup"><span data-stu-id="b369e-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="b369e-107">Il s’agit de l’événement est déclenché lorsque l’utilisateur passe d’un onglet à l’autre.</span><span class="sxs-lookup"><span data-stu-id="b369e-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2.  <span data-ttu-id="b369e-108">Vérifiez les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="b369e-108">Check credentials.</span></span> <span data-ttu-id="b369e-109">Selon les informations présentées, vous voudrez vérifier l’utilisateur a ouvert une session avec le nom d’utilisateur ou d’une autre forme d’informations d’identification avant d’autoriser l’utilisateur d’afficher l’onglet.</span><span class="sxs-lookup"><span data-stu-id="b369e-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3.  <span data-ttu-id="b369e-110">Si l’utilisateur dispose des informations d’identification appropriées, affichez l’onglet que vous avez cliqué.</span><span class="sxs-lookup"><span data-stu-id="b369e-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="b369e-111">Si l’utilisateur n’a pas d’informations d’identification appropriées, afficher une boîte de message ou une autre interface d’utilisateur indiquant qu’ils ne pas avoir accès et revenir à l’onglet initial.</span><span class="sxs-lookup"><span data-stu-id="b369e-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b369e-112">Lorsque vous implémentez cette fonctionnalité dans vos applications de production, vous pouvez effectuer cette vérification des informations d’identification au cours du formulaire <xref:System.Windows.Forms.Form.Load> événement.</span><span class="sxs-lookup"><span data-stu-id="b369e-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="b369e-113">Cela vous permettra de masquer l’onglet avant l’affichage de n’importe quelle interface utilisateur, ce qui constitue une approche beaucoup plus propre de la programmation.</span><span class="sxs-lookup"><span data-stu-id="b369e-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="b369e-114">La méthodologie utilisée ci-dessous (vérification des informations d’identification et la désactivation de l’onglet au cours de la <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> événement) est à titre d’illustration.</span><span class="sxs-lookup"><span data-stu-id="b369e-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4.  <span data-ttu-id="b369e-115">Si vous le souhaitez, si vous avez plus de deux pages d’onglets, afficher une page différente de la version d’origine.</span><span class="sxs-lookup"><span data-stu-id="b369e-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="b369e-116">Dans l’exemple ci-dessous, un <xref:System.Windows.Forms.CheckBox> contrôle est utilisé au lieu de vérifier les informations d’identification, comme critère pour accéder à l’onglet peuvent varier selon l’application.</span><span class="sxs-lookup"><span data-stu-id="b369e-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="b369e-117">Lorsque le <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> événement est déclenché si la vérification des informations d’identification a la valeur true (autrement dit, la case à cocher est activée) et l’onglet sélectionné est `TabPage2` (onglet avec les informations confidentielles, dans cet exemple), puis `TabPage2` s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b369e-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="b369e-118">Sinon, `TabPage3` s’affiche et un message s’affiche à l’utilisateur, indiquant qu’ils n’ont pas de privilèges d’accès appropriés.</span><span class="sxs-lookup"><span data-stu-id="b369e-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="b369e-119">Le code ci-dessous illustre un formulaire avec un <xref:System.Windows.Forms.CheckBox> contrôle (`CredentialCheck`) et un <xref:System.Windows.Forms.TabControl> contrôle avec trois pages d’onglets.</span><span class="sxs-lookup"><span data-stu-id="b369e-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="b369e-120">(Visual c#, Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="b369e-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b369e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b369e-121">See Also</span></span>  
 [<span data-ttu-id="b369e-122">Vue d’ensemble du contrôle TabControl</span><span class="sxs-lookup"><span data-stu-id="b369e-122">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="b369e-123">Guide pratique pour ajouter un contrôle à une page d'onglet</span><span class="sxs-lookup"><span data-stu-id="b369e-123">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="b369e-124">Guide pratique pour ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b369e-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="b369e-125">Guide pratique pour modifier l'apparence du contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b369e-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
