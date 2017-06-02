---
title: "Comment&#160;: associer un menu contextuel &#224; un composant NotifyIcon Windows Forms | Microsoft Docs"
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
  - "menus contextuels, pour les processus d'arrière-plan"
  - "NotifyIcon (composant), associer des menus contextuels"
  - "menus contextuels, pour les processus d'arrière-plan"
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: associer un menu contextuel &#224; un composant NotifyIcon Windows Forms
> [!NOTE]
>  Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacent les contrôles <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> des versions précédentes et leur ajoutent des fonctionnalités, <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et une utilisation future, si tel est votre choix.  
  
 Le composant <xref:System.Windows.Forms.NotifyIcon> Windows Forms affiche une icône dans la zone d'état de la barre des tâches.  En général, les applications autorisent l'utilisateur à cliquer avec le bouton droit sur cette icône afin d'envoyer des commandes à l'application qu'elle représente.  En associant un composant <xref:System.Windows.Forms.ContextMenu> au composant <xref:System.Windows.Forms.NotifyIcon>, vous pouvez ajouter ces fonctionnalités à vos applications.  
  
> [!NOTE]
>  Si vous souhaitez que votre application soit réduite au démarrage en affichant une instance du composant <xref:System.Windows.Forms.NotifyIcon> dans la barre des tâches, définissez la propriété <xref:System.Windows.Forms.Form.WindowState%2A> du formulaire principal à <xref:System.Windows.Forms.FormWindowState> et veillez à attribuer à la propriété <xref:System.Windows.Forms.NotifyIcon.Visible%2A> du composant <xref:System.Windows.Forms.NotifyIcon> la valeur `true`.  
  
### Pour associer un menu contextuel à un composant NotifyIcon au moment du design  
  
1.  Ajoutez un composant <xref:System.Windows.Forms.NotifyIcon> à votre formulaire et définissez les propriétés importantes, telles que <xref:System.Windows.Forms.NotifyIcon.Icon%2A> et <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.  
  
     Pour plus d'informations, consultez [Comment : ajouter des icônes d'application à la barre des tâches à l'aide du composant NotifyIcon Windows Forms](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2.  Ajoutez un composant <xref:System.Windows.Forms.ContextMenu> à votre Windows Form.  
  
     Ajoutez des éléments de menu au menu contextuel qui représente les commandes que vous souhaitez rendre disponibles lors de l'exécution.  C'est également le moment opportun pour ajouter des améliorations à ces éléments de menu, notamment des touches d'accès rapide.  
  
3.  Définissez la propriété <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> du composant <xref:System.Windows.Forms.NotifyIcon> approprié en fonction du menu contextuel que vous avez ajouté.  
  
     Cette propriété étant définie, le menu contextuel s'affiche lorsque l'utilisateur clique sur l'icône dans la barre des tâches.  
  
### Pour associer un menu contextuel au composant NotifyIcon par programme  
  
1.  Créez une instance de la classe <xref:System.Windows.Forms.NotifyIcon> et une classe <xref:System.Windows.Forms.ContextMenu>, avec les paramètres de propriété qui sont nécessaires pour l'application \(les propriétés <xref:System.Windows.Forms.NotifyIcon.Icon%2A> et <xref:System.Windows.Forms.NotifyIcon.Visible%2A> pour le composant <xref:System.Windows.Forms.NotifyIcon>, des éléments de menu pour le composant <xref:System.Windows.Forms.ContextMenu>\).  
  
2.  Définissez la propriété <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> du composant <xref:System.Windows.Forms.NotifyIcon> approprié en fonction du menu contextuel que vous avez ajouté.  
  
     Cette propriété étant définie, le menu contextuel s'affiche lorsque l'utilisateur clique sur l'icône dans la barre des tâches.  
  
    > [!NOTE]
    >  L'exemple de code qui suit crée une structure de menu élémentaire.  Vous devrez personnaliser les options de menu en fonction de l'application que vous développez.  Vous devez également écrire le code permettant de gérer les événements <xref:System.Windows.Forms.MenuItem.Click> pour ces options de menu.  
  
    ```vb  
    Public ContextMenu1 As New ContextMenu  
    Public NotifyIcon1 As New NotifyIcon  
  
    Public Sub CreateIconMenuStructure()  
       ' Add menu items to shortcut menu.  
       ContextMenu1.MenuItems.Add("&Open Application")  
       ContextMenu1.MenuItems.Add("S&uspend Application")  
       ContextMenu1.MenuItems.Add("E&xit")  
  
       ' Set properties of NotifyIcon component.  
       NotifyIcon1.Icon = New System.Drawing.Icon _   
          (System.Environment.GetFolderPath _   
          (System.Environment.SpecialFolder.Personal)  _   
          & "\Icon.ico")  
       NotifyIcon1.Text = "Right-click me!"  
       NotifyIcon1.Visible = True  
       NotifyIcon1.ContextMenu = ContextMenu1  
    End Sub  
  
    ```  
  
```csharp  
public NotifyIcon notifyIcon1 = new NotifyIcon();  
public ContextMenu contextMenu1 = new ContextMenu();  
  
public void createIconMenuStructure()  
{  
   // Add menu items to shortcut menu.  
   contextMenu1.MenuItems.Add("&Open Application");  
   contextMenu1.MenuItems.Add("S&uspend Application");  
   contextMenu1.MenuItems.Add("E&xit");  
  
   // Set properties of NotifyIcon component.  
   notifyIcon1.Icon = new System.Drawing.Icon  
      (System.Environment.GetFolderPath  
      (System.Environment.SpecialFolder.Personal)  
      + @"\Icon.ico");  
   notifyIcon1.Visible = true;  
   notifyIcon1.Text = "Right-click me!";  
   notifyIcon1.Visible = true;  
   notifyIcon1.ContextMenu = contextMenu1;  
}  
  
```  
  
```cpp  
public:  
   System::Windows::Forms::NotifyIcon ^ notifyIcon1;  
   System::Windows::Forms::ContextMenu ^ contextMenu1;  
  
   void createIconMenuStructure()  
   {  
      // Add menu items to shortcut menu.  
      contextMenu1->MenuItems->Add("&Open Application");  
      contextMenu1->MenuItems->Add("S&uspend Application");  
      contextMenu1->MenuItems->Add("E&xit");  
  
      // Set properties of NotifyIcon component.  
      notifyIcon1->Icon = gcnew System::Drawing::Icon  
          (String::Concat(System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::Personal),  
          "\\Icon.ico"));  
      notifyIcon1->Text = "Right-click me!";  
      notifyIcon1->Visible = true;  
      notifyIcon1->ContextMenu = contextMenu1;  
   }  
```  
  
> [!NOTE]
>  Vous devez initialiser `notifyIcon1` et `contextMenu1,` en incluant les instructions suivantes dans le constructeur de votre formulaire :  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## Voir aussi  
 <xref:System.Windows.Forms.NotifyIcon>   
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>   
 [Comment : ajouter des icônes d'application à la barre des tâches à l'aide du composant NotifyIcon Windows Forms](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)   
 [NotifyIcon, composant](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)   
 [Vue d'ensemble du composant NotifyIcon](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)