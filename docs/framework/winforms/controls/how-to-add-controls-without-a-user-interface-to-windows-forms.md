---
title: "Comment&#160;: ajouter des contr&#244;les sans interface utilisateur &#224; des Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NonVisualSelection"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles (Windows Forms), non visuels"
  - "contrôles invisibles"
  - "contrôles non visuels"
  - "contrôles Windows Forms, ajouter aux formulaires"
  - "contrôles Windows Forms, non visuels"
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: ajouter des contr&#244;les sans interface utilisateur &#224; des Windows Forms
Les contrôles \(ou composants\) non visuels apportent des fonctionnalités à votre application.  À la différence des autres contrôles, les composants ne fournissent pas d'interface d'utilisateur et n'ont, par conséquent, pas besoin d'être affichés sur la surface du Concepteur Windows Forms.  Lorsqu'un composant est ajouté à un formulaire, le Concepteur Windows Forms affiche, au bas du formulaire, une barre redimensionnable dans laquelle sont présentés tous les composants.  Une fois qu'un contrôle a été ajouté à la barre d'état des composants, vous pouvez le sélectionner et définir ses propriétés comme vous le feriez avec n'importe quel contrôle du formulaire.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour ajouter un composant à un Windows Form  
  
1.  Ouvrez le formulaire.  Pour plus d'informations, consultez [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/fr-fr/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  Dans la **Boîte à outils**, cliquez sur un composant et faites\-le glisser jusqu'à votre formulaire.  
  
     Il apparaît alors dans la barre d'état des composants.  
  
 En outre, il est possible d'ajouter des composants à un formulaire au moment de l'exécution.  Il s'agit d'un scénario fréquent, car les composants ne possèdent pas d'expression visuelle, contrairement aux contrôles \(qui disposent d'une interface utilisateur\).  Dans l'exemple ci\-dessous, un composant <xref:System.Windows.Forms.Timer> est ajouté au moment de l'exécution.  \(Notez que [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] contient différents types de minuteries \(Timers\) ; dans ce cas, utilisez un composant <xref:System.Windows.Forms.Timer> Windows Forms.  Pour plus d'informations sur les différentes minuteries \(Timers\) présentes dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], consultez [Introduction to Server\-Based Timers](http://msdn.microsoft.com/fr-fr/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).\)  
  
> [!CAUTION]
>  Les composants possèdent souvent des propriétés spécifiques au contrôle qui doivent être définies pour qu'ils puissent fonctionner correctement.  Dans le cas du composant <xref:System.Windows.Forms.Timer> de l'exemple ci\-dessous, vous devez définir la propriété `Interval`.  Lorsque vous ajoutez des composants à votre projet, veillez à définir les propriétés nécessaires à ce composant.  
  
#### Pour ajouter par programme un composant à un Windows Form  
  
1.  Créez une instance de la classe <xref:System.Windows.Forms.Timer> dans le code.  
  
2.  Définissez la propriété `Interval` pour déterminer l'intervalle entre les graduations de la minuterie \(Timer\).  
  
3.  Configurez toutes les autres propriétés nécessaires à votre composant.  
  
     Le code suivant montre comment créer un objet <xref:System.Windows.Forms.Timer> et définir sa propriété `Interval`.  
  
    ```vb  
    Public Sub CreateTimer()  
       Dim timerKeepTrack As New System.Windows.Forms.Timer  
       timerKeepTrack.Interval = 1000  
    End Sub  
  
    ```  
  
    ```csharp  
    public void createTimer()  
    {  
       System.Windows.Forms.Timer timerKeepTrack = new  
           System.Windows.Forms.Timer();  
       timerKeepTrack.Interval = 1000;  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void createTimer()  
       {  
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew  
             System::Windows::Forms::Timer();  
          timerKeepTrack->Interval = 1000;  
       }  
    ```  
  
    > [!IMPORTANT]
    >  Vous risquez d'exposer votre ordinateur local à un problème de sécurité sur le réseau si vous référencez un UserControl nuisible.  Ce risque est présent dans le cas d'une personne malveillante qui crée un contrôle personnalisé préjudiciable, si vous ajoutez par erreur ce contrôle à votre projet.  
  
## Voir aussi  
 [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)   
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)   
 [Comment : ajouter des contrôles ActiveX aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)   
 [Comment : copier des contrôles entre des Windows Forms](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)   
 [Placement de contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)   
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)