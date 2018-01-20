---
title: "Comment : ajouter des contrôles sans interface utilisateur à des Windows Forms"
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
f1_keywords: NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3abbf931cff9ad459e8c9221f91430ecccefa9cc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Comment : ajouter des contrôles sans interface utilisateur à des Windows Forms
Un contrôle non visuel (ou un composant) fournit des fonctionnalités à votre application. Contrairement à d’autres contrôles, les composants ne fournissent pas d’interface utilisateur à l’utilisateur et par conséquent, n’avez pas besoin être affiché sur l’aire du Concepteur Windows Forms. Lorsqu’un composant est ajouté à un formulaire, le Concepteur Windows Forms affiche une barre d’état redimensionnable au bas de l’écran où tous les composants sont affichés. Une fois qu’un contrôle a été ajouté à la barre d’état du composant, vous pouvez sélectionner le composant et définissez ses propriétés comme vous le feriez pour tout autre contrôle sur le formulaire.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-component-to-a-windows-form"></a>Pour ajouter un composant à un Windows Form  
  
1.  Ouvrez le formulaire. Pour plus d’informations, consultez [Comment : afficher des Windows Forms dans le concepteur](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  Dans le **boîte à outils**, cliquez sur un composant et faites-le glisser vers votre formulaire.  
  
     Votre composant s’affiche dans la barre d’état du composant.  
  
 En outre, les composants peuvent être ajoutés à un formulaire au moment de l’exécution. Il s’agit d’un scénario courant, en particulier, car les composants n’ont pas de représentation visuelle, contrairement aux contrôles qui ont une interface utilisateur. Dans l’exemple ci-dessous, un <xref:System.Windows.Forms.Timer> composant est ajouté au moment de l’exécution. (Notez que [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] contient un numéro de différents types de minuteries ; dans ce cas, utilisez un Windows Forms <xref:System.Windows.Forms.Timer> composant. Pour plus d’informations sur les différentes minuteries dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], consultez [Introduction aux minuteurs serveur](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)  
  
> [!CAUTION]
>  Composants ont souvent des propriétés spécifiques au contrôle qui doivent être définies pour le composant de fonctionner efficacement. Dans le cas de la <xref:System.Windows.Forms.Timer> composant ci-dessous, vous définissez le `Interval` propriété. Assurez-vous que, lors de l’ajout de composants à votre projet, définissez les propriétés nécessaires à ce composant.  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a>Pour ajouter un composant à un Windows Form par programmation  
  
1.  Créez une instance de la <xref:System.Windows.Forms.Timer> classe dans le code.  
  
2.  Définir le `Interval` propriété pour déterminer l’intervalle entre les graduations de la minuterie.  
  
3.  Configurez toutes les autres propriétés nécessaires pour votre composant.  
  
     Le code suivant illustre la création d’un <xref:System.Windows.Forms.Timer> avec son `Interval` jeu de propriétés.  
  
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
    >  Vous pouvez exposer votre ordinateur local à un risque de sécurité via le réseau en référençant un UserControl malveillant. Il s’agit uniquement d’un problème dans le cas d’une personne malveillante, créer un contrôle personnalisé causer des dommages, suivi de vous ajouter par erreur à votre projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Guide pratique pour ajouter des contrôles ActiveX aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [Guide pratique pour copier des contrôles entre des Windows Forms](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [Placement de contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
