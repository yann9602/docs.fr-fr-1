---
title: "Vue d'ensemble des boîtes de dialogue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 112a9badaf9a64b2c6d3f73d64c27fbc36ec48a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="dialog-boxes-overview"></a>Vue d'ensemble des boîtes de dialogue
Les applications autonomes ont généralement une fenêtre principale qui affiche les données principales sur lesquelles l’application fonctionne et expose les fonctionnalités pour traiter ces données via [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mécanismes tels que les barres de menus, barres d’outils et barres d’état. Une application non triviale peut également afficher des fenêtres supplémentaires pour effectuer les opérations suivantes :  
  
-   Présenter des informations spécifiques aux utilisateurs  
  
-   Recueillir des informations auprès des utilisateurs  
  
-   Afficher et recueillir des informations  
  
 Ces types de fenêtres sont appelés *boîtes de dialogue*, et il existe deux types : modales et non modales.  
  
 A *modale* boîte de dialogue est affichée par une fonction quand la fonction a besoin de données supplémentaires à partir d’un utilisateur à se poursuivre. Étant donné que la fonction dépend de la boîte de dialogue modale pour recueillir des données, celle-ci empêche également un utilisateur d’activer d’autres fenêtres de l’application pendant qu’elle reste ouverte. Dans la plupart des cas, une boîte de dialogue modale permet à un utilisateur signaler lorsqu’ils ont terminé avec la boîte de dialogue modale en appuyant sur soit un **OK** ou **Annuler** bouton. En appuyant sur la **OK** bouton indique qu’un utilisateur a entré des données et souhaite que la fonction pour continuer le traitement avec ces données. En appuyant sur la **Annuler** bouton indique qu’un utilisateur souhaite arrêter la fonction complètement l’exécution. Les exemples les plus courants de boîtes de dialogue modales sont présentés pour ouvrir, enregistrer et imprimer des données.  
  
 A *non modale* boîte de dialogue, en revanche, n’empêche pas un utilisateur d’activer d’autres fenêtres lorsqu’il est ouvert. Par exemple, si un utilisateur souhaite rechercher des occurrences d’un mot particulier dans un document, une fenêtre principale peut ouvrir une boîte de dialogue pour l’inviter à spécifier le mot qu’il recherche. Puisque rechercher un mot n’empêche pas l’utilisateur de modifier le document, la boîte de dialogue n’a pas besoin d’être modale. Une boîte de dialogue non modale fournit au moins un **fermer** bouton pour fermer la boîte de dialogue et peut fournir des boutons supplémentaires pour exécuter des fonctions spécifiques, comme un **suivant** bouton pour rechercher la prochaine les mots correspond aux critères de recherche d’une recherche de mots.  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] vous permet de créer plusieurs types de boîtes de dialogue, notamment des boîtes de message, des boîtes de dialogue communes et des boîtes de dialogue personnalisées. Cette rubrique présente chacune et le [exemple de boîte de dialogue](http://go.microsoft.com/fwlink/?LinkID=159984) fournit des exemples correspondants.  
  
 
  
<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>Boîtes de message  
 A *boîte de message* est une boîte de dialogue qui peut être utilisée pour afficher des informations textuelles et permettre aux utilisateurs de prendre des décisions avec des boutons. L’illustration suivante montre une boîte de message qui affiche des informations textuelles, pose une question et fournit à l’utilisateur trois boutons pour répondre à la question.  
  
 ![Boîte de dialogue de traitement de texte](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure1.png "DialogBoxesOverviewFigure1")  
  
 Pour créer une boîte de message, vous utilisez la <xref:System.Windows.MessageBox> classe. <xref:System.Windows.MessageBox>vous permet de configurer le texte du message, un titre, une icône et un boutons, à l’aide de code semblable au suivant.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Pour afficher une boîte de message, vous appelez le `static` <xref:System.Windows.MessageBox.Show%2A> méthode, comme illustré dans le code suivant.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Quand le code qui affiche une boîte de message doit détecter et traiter la décision de l’utilisateur (quel bouton a été enfoncé), le code peut inspecter le résultat de la boîte de message, comme indiqué dans le code suivant.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 Pour plus d’informations sur l’utilisation des boîtes de message, consultez <xref:System.Windows.MessageBox>, [MessageBox, exemple](http://go.microsoft.com/fwlink/?LinkID=160023), et [exemple de boîte de dialogue](http://go.microsoft.com/fwlink/?LinkID=159984).  
  
 Bien que <xref:System.Windows.MessageBox> peut offrir une expérience utilisateur de boîte dialogue simple, l’avantage d’utiliser <xref:System.Windows.MessageBox> qui est le seul type de fenêtre qui peut être affiché par les applications qui s’exécutent dans un sandbox de sécurité de confiance partielle (consultez [sécurité](../../../../docs/framework/wpf/security-wpf.md)), tel que [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
 La plupart des boîtes de dialogue affichent et recueillent des données plus complexes que le résultat d’une boîte de message, notamment du texte, une sélection (cases à cocher), une sélection mutuellement exclusive (boutons radio) et une sélection dans une liste (zones de liste, zones de liste modifiable, zones de liste déroulante). Dans ce cas, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] fournit plusieurs boîtes de dialogue communes et vous permet de créer vos propres boîtes de dialogue, bien que l’utilisation d’un est limitée aux applications s’exécutant avec une confiance totale.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Boîtes de dialogue communes  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] implémente diverses boîtes de dialogue réutilisables qui sont communes à toutes les applications, notamment des boîtes de dialogue pour ouvrir, enregistrer et imprimer des fichiers. Ces boîtes de dialogue étant implémentées par le système d’exploitation, elles peuvent être partagées par toutes les applications qui s’exécutent sur le système d’exploitation, ce qui favorise la cohérence de l’expérience utilisateur. Quand les utilisateurs sont habitués à utiliser une boîte de dialogue fournie par le système d’exploitation dans une application, ils n’ont pas besoin d’apprendre à utiliser cette boîte de dialogue dans d’autres applications. Étant donné que ces boîtes de dialogue sont disponibles pour toutes les applications et car ils permettent de fournir une expérience utilisateur cohérente, ils sont appelés *boîtes de dialogue communes*.  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] encapsule les boîtes de dialogue communes d’ouverture, d’enregistrement et d’impression de fichier, et les expose en tant que classes managées pour que vous puissiez les utiliser dans des applications autonomes. Cette rubrique fournit une brève présentation de chacune de ces boîtes de dialogue.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Boîte de dialogue d’ouverture de fichier  
 La boîte de dialogue d’ouverture de fichier, illustrée ci-dessous, est utilisée par la fonctionnalité d’ouverture de fichier pour récupérer le nom d’un fichier à ouvrir.  
  
 ![Boîte de dialogue Ouvrir](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure2.png "DialogBoxesOverviewFigure2")  
  
 La boîte de dialogue Ouvrir un fichier est implémentée en tant que le <xref:Microsoft.Win32.OpenFileDialog> classe et se trouve dans le <xref:Microsoft.Win32> espace de noms. Le code suivant montre comment en créer, configurer et afficher une, et comment traiter le résultat.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Pour plus d’informations sur la boîte de dialogue Ouvrir un fichier, consultez <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog>peut servir à récupérer en toute sécurité des noms de fichiers par les applications qui s’exécutent avec une confiance partielle (consultez [sécurité](../../../../docs/framework/wpf/security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>Boîte de dialogue d’enregistrement de fichier  
 La boîte de dialogue d’enregistrement de fichier, illustrée ci-dessous, est utilisée par la fonctionnalité d’enregistrement de fichier pour récupérer le nom d’un fichier à enregistrer.  
  
 ![Boîte de dialogue Enregistrer sous](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure3.png "DialogBoxesOverviewFigure3")  
  
 Enregistrer la boîte de dialogue de fichier courantes est implémenté en tant que le <xref:Microsoft.Win32.SaveFileDialog> de classe et se trouve dans le <xref:Microsoft.Win32> espace de noms. Le code suivant montre comment en créer, configurer et afficher une, et comment traiter le résultat.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Pour plus d’informations sur l’enregistrement de fichiers de boîte de dialogue, consultez <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Boîte de dialogue d’impression  
 La boîte de dialogue d’impression, illustrée ci-dessous, est utilisée par la fonctionnalité d’impression pour choisir et configurer l’imprimante sur laquelle un utilisateur souhaite imprimer des données.  
  
 ![Boîte de dialogue Imprimer](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure4.png "DialogBoxesOverviewFigure4")  
  
 La boîte de dialogue d’impression est implémentée en tant que le <xref:System.Windows.Controls.PrintDialog> de classe et se trouve dans le <xref:System.Windows.Controls> espace de noms. Le code suivant montre comment en créer, configurer et afficher une.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Pour plus d’informations sur la boîte de dialogue d’impression, consultez <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Pour une présentation détaillée de l’impression dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consultez [vue d’ensemble de l’impression](../../../../docs/framework/wpf/advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Boîtes de dialogue personnalisées  
 Bien que les boîtes de dialogue communes soient utiles (et doivent être utilisées dans la mesure du possible), elles ne prennent pas en charge les exigences des boîtes de dialogue propres au domaine. Dans ces cas-là, vous devez créer vos propres boîtes de dialogue. Comme nous allons le voir, une boîte de dialogue est une fenêtre avec des comportements spéciaux. <xref:System.Windows.Window>implémente ces comportements et, par conséquent, vous utilisez <xref:System.Windows.Window> pour créer des zones de la boîte de dialogue modales et non modales personnalisée.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Création d’une boîte de dialogue personnalisée modale  
 Cette rubrique montre comment utiliser <xref:System.Windows.Window> pour créer une implémentation de boîte de dialogue modale type, à l’aide de la `Margins` boîte de dialogue par exemple (voir [boîte de dialogue, exemple](http://go.microsoft.com/fwlink/?LinkID=159984)). Le `Margins` boîte de dialogue est affichée dans l’illustration suivante.  
  
 ![Boîte de dialogue Margins](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure5.png "DialogBoxesOverviewFigure5")  
  
#### <a name="configuring-a-modal-dialog-box"></a>Configuration d’une boîte de dialogue modale  
 L’interface utilisateur pour une boîte de dialogue classique comprend les éléments suivants :  
  
-   Les différents contrôles nécessaires pour recueillir les données souhaitées  
  
-   Affichant un **OK** bouton que les utilisateurs cliquez sur pour fermer la boîte de dialogue, retour à la fonction et continuer le traitement.  
  
-   Affichant un **Annuler** bouton sur lequel les utilisateurs cliquent sur pour fermer la boîte de dialogue et arrêter la traitement de la fonction.  
  
-   Affichant un **fermer** bouton dans la barre de titre.  
  
-   Une icône  
  
-   Affichage **réduire**, **agrandir**, et **restaurer** boutons.  
  
-   Affichant un **système** menu pour réduire, agrandir, restaurer et fermer la boîte de dialogue.  
  
-   L’ouverture par-dessus et au centre de la fenêtre qui a ouvert la boîte de dialogue  
  
-   Les boîtes de dialogue doivent être redimensionnables dans la mesure du possible. Ainsi, pour empêcher que la boîte de dialogue soit trop petite et pour proposer à l’utilisateur une taille par défaut utile, vous devez définir respectivement des dimensions par défaut et minimales.  
  
-   Appuyez sur la touche ÉCHAP doit être configuré comme un raccourci clavier qui provoque le **Annuler** bouton. Cela s’effectue en définissant le <xref:System.Windows.Controls.Button.IsCancel%2A> propriété de la **Annuler** bouton à `true`.  
  
-   Appuyez sur la touche entrée (ou retour) doit être configuré comme un raccourci clavier qui provoque le **OK** bouton. Cela s’effectue en définissant le <xref:System.Windows.Controls.Button.IsDefault%2A> propriété de la **OK** bouton `true`.  
  
 Le code suivant illustre cette configuration.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 L’expérience utilisateur pour une boîte de dialogue s’étend également à la barre de menus de la fenêtre qui ouvre la boîte de dialogue. Quand un élément de menu exécute une fonction qui nécessite une interaction utilisateur par l’intermédiaire d’une boîte de dialogue pour que la fonction puisse se poursuivre, l’élément de menu de la fonction a des points de suspension dans son en-tête, comme illustré ici.  
  
 [!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 Quand un élément de menu exécute une fonction qui affiche une boîte de dialogue qui ne nécessite pas d’intervention de l’utilisateur, par exemple une boîte de dialogue À propos, les points de suspension ne sont pas nécessaires.  
  
#### <a name="opening-a-modal-dialog-box"></a>Ouverture d’une boîte de dialogue modale  
 Une boîte de dialogue apparaît généralement quand un utilisateur sélectionne un élément de menu pour exécuter une fonction propre à un domaine, par exemple pour définir les marges d’un document dans un traitement de texte. Afficher une fenêtre sous forme de boîte de dialogue s’apparente à afficher une fenêtre normale, bien que cela nécessite une configuration supplémentaire propre à la boîte de dialogue. L’ensemble du processus d’instanciation, de configuration et d’ouverture d’une boîte de dialogue est illustré dans le code suivant.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 Ici, le code passe des informations par défaut (les marges actuelles) à la boîte de dialogue. Il configure également le <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> propriété avec une référence à la fenêtre qui affiche la boîte de dialogue. En règle générale, vous devez toujours définir le propriétaire d’une boîte de dialogue pour fournir des comportements liés à l’état de fenêtre qui sont communes à toutes les boîtes de dialogue (consultez [WPF Windows Overview](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md) pour plus d’informations).  
  
> [!NOTE]
>  Vous devez indiquer un propriétaire pour prendre en charge [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] automation pour les boîtes de dialogue (consultez [UI Automation Overview](../../../../docs/framework/ui-automation/ui-automation-overview.md)).  
  
 Une fois la boîte de dialogue est configurée, il est affiché sous forme modale en appelant le <xref:System.Windows.Window.ShowDialog%2A> (méthode).  
  
#### <a name="validating-user-provided-data"></a>Validation des données fournies par l’utilisateur  
 Quand une boîte de dialogue est ouverte et que l’utilisateur fournit les données requises, une boîte de dialogue est chargée de vérifier que les données fournies sont valides pour les raisons suivantes :  
  
-   Du point de vue de la sécurité, toutes les entrées doivent être validées.  
  
-   D’un point de vue propre au domaine, la validation des données empêche que des données erronées soient traitées par le code, ce qui pourrait éventuellement lever des exceptions.  
  
-   Du point de vue de l’expérience utilisateur, une boîte de dialogue peut aider les utilisateurs en leur montrant lesquelles des données entrées ne sont pas valides.  
  
-   Du point de vue des performances, la validation des données dans une application multicouche peut réduire le nombre d’allers-retours entre le client et les couches Application, en particulier quand l’application est composée de services web ou de bases de données basées sur serveur.  
  
 Pour valider un contrôle dépendant dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vous devez définir une règle de validation et l’associer à la liaison. Une règle de validation est une classe personnalisée qui dérive de <xref:System.Windows.Controls.ValidationRule>. L’exemple suivant montre une règle de validation, `MarginValidationRule`, qui vérifie qu’une valeur liée est un <xref:System.Double> et se trouve dans une plage spécifiée.  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 Dans ce code, la logique de validation d’une règle de validation est implémentée en substituant la <xref:System.Windows.Controls.ValidationRule.Validate%2A> (méthode), ce qui valide les données et retourne une fonction <xref:System.Windows.Controls.ValidationResult>.  
  
 Pour associer la règle de validation au contrôle dépendant, vous utilisez le balisage suivant.  
  
 [!code-xaml[DialogBoxSample#MarginsValidationMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 Une fois que la règle de validation est associée, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] appliquera automatiquement lorsque les données entrées dans le contrôle dépendant. Lorsqu’un contrôle contient des données non valides, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] affichera une bordure rouge autour du contrôle non valide, comme indiqué dans l’illustration suivante.  
  
 ![Marge gauche non valide](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure7.png "DialogBoxesOverviewFigure7")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] n’empêche pas l’utilisateur de sortir du contrôle non valide s’il n’a pas entré des données valides. Il s’agit d’un bon comportement pour une boîte de dialogue. En effet, un utilisateur doit pouvoir naviguer librement entre les contrôles d’une boîte de dialogue, que les données soient valides ou non. Toutefois, cela signifie un utilisateur peut entrer des données non valides, puis appuyez sur la **OK** bouton. Pour cette raison, votre code doit également valider tous les contrôles dans une boîte de dialogue boîte lorsque le **OK** bouton est enfoncé en gérant la <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 Ce code énumère tous les objets de dépendance sur une fenêtre et, si une est non valide (telle que retournée par <xref:System.Windows.Controls.Validation.GetHasError%2A>, le contrôle non valide Obtient le focus, le `IsValid` méthode retourne `false`, et la fenêtre est considéré comme non valide.  
  
 Une fois qu’une boîte de dialogue est valide, elle peut être fermée et retourner un résultat en toute sécurité. Dans le cadre du processus de retour, elle doit retourner un résultat à la fonction appelante.  
  
#### <a name="setting-the-modal-dialog-result"></a>Définition du résultat de la boîte de dialogue modale  
 Ouverture d’un à l’aide de la boîte de dialogue <xref:System.Windows.Window.ShowDialog%2A> est fondamentalement à appeler une méthode : le code qui a ouvert la boîte de dialogue à l’aide de <xref:System.Windows.Window.ShowDialog%2A> attend <xref:System.Windows.Window.ShowDialog%2A> retourne. Lorsque <xref:System.Windows.Window.ShowDialog%2A> retourne, le code qui l’a appelée a besoin pour décider s’il faut poursuivre le traitement ou d’arrêter le traitement, selon si l’utilisateur a appuyé sur le **OK** bouton ou le **Annuler** bouton. Pour faciliter cette décision, la boîte de dialogue doit retourner le choix de l’utilisateur comme un <xref:System.Boolean> valeur retournée à partir de la <xref:System.Windows.Window.ShowDialog%2A> (méthode).  
  
 Lorsque le **OK** bouton est activé, <xref:System.Windows.Window.ShowDialog%2A> doit retourner `true`. Cela s’effectue en définissant le <xref:System.Windows.Window.DialogResult%2A> boîte de propriété de la boîte de dialogue lorsque le **OK** bouton.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 Notez que la définition du <xref:System.Windows.Window.DialogResult%2A> propriété entraîne également la fenêtre se ferme automatiquement, ce qui permet de ne pas appeler explicitement <xref:System.Windows.Window.Close%2A>.  
  
 Lorsque le **Annuler** bouton est activé, <xref:System.Windows.Window.ShowDialog%2A> doit retourner `false`, qui requiert également la définition du <xref:System.Windows.Window.DialogResult%2A> propriété.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 Lorsqu’un bouton de <xref:System.Windows.Controls.Button.IsCancel%2A> est définie sur `true` , l’utilisateur appuie sur un le **Annuler** bouton ou la touche ÉCHAP, <xref:System.Windows.Window.DialogResult%2A> est automatiquement défini sur `false`. La balise suivante a le même effet que le code précédent, sans avoir à gérer le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 Une boîte de dialogue retourne automatiquement `false` lorsqu’un utilisateur appuie sur le **fermer** bouton dans la barre de titre ou s’il choisit la **fermer** élément de menu à partir de la **système** menu.  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Traitement des données retournées par la boîte de dialogue modale  
 Lorsque <xref:System.Windows.Window.DialogResult%2A> est défini par une boîte de dialogue, la fonction qui l’a ouvert peut obtenir le résultat de la boîte de dialogue en inspectant la <xref:System.Windows.Window.DialogResult%2A> propriété lorsque <xref:System.Windows.Window.ShowDialog%2A> renvoie.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 Si le résultat de la boîte de dialogue est `true`, la fonction utilise comme une file d’attente pour récupérer et traiter les données fournies par l’utilisateur.  
  
> [!NOTE]
>  Après avoir <xref:System.Windows.Window.ShowDialog%2A> a retourné, une boîte de dialogue ne peut pas être rouverte. Au lieu de cela, vous devez créer une nouvelle instance.  
  
 Si le résultat de la boîte de dialogue est `false`, la fonction doit terminer le traitement de façon appropriée.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Création d’une boîte de dialogue personnalisée non modale  
 Une boîte de dialogue non modale, telle que la boîte de dialogue Rechercher affichée ci-dessous, a la même apparence fondamentale que la boîte de dialogue modale.  
  
 ![Boîte de dialogue Rechercher](../../../../docs/framework/wpf/app-development/media/dialogboxesoverviewfigure6.PNG "DialogBoxesOverviewFigure6")  
  
 Toutefois, le comportement est légèrement différent, comme décrit dans les sections suivantes.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Ouverture d’une boîte de dialogue non modale  
 Une boîte de dialogue non modale est ouverte en appelant le <xref:System.Windows.Window.Show%2A> (méthode).  
  
 [!code-xaml[DialogBoxSample#OpenFindDialogMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 Contrairement aux <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> retourne immédiatement. Ainsi, la fenêtre appelante ne peut pas savoir quand la boîte de dialogue non modale est fermée, et ne sait pas quand vérifier le résultat d’une boîte de dialogue ou obtenir des données à partir de la boîte de dialogue pour un traitement ultérieur. Au lieu de cela, la boîte de dialogue doit créer un autre moyen pour retourner des données à la fenêtre appelante en vue de leur traitement.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Traitement des données retournées par la boîte de dialogue non modale  
 Dans cet exemple, le `FindDialogBox` peut retourner un ou plusieurs résultats à la fenêtre principale, selon le texte recherché sans fréquence spécifique de la recherche. Comme avec une boîte de dialogue modale, une boîte de dialogue non modale peut retourner des résultats à l’aide de propriétés. Toutefois, la fenêtre propriétaire de la boîte de dialogue doit savoir quand vérifier ces propriétés. L’une des solutions consiste à ce que la boîte de dialogue implémente un événement déclenché chaque fois que le texte est trouvé. `FindDialogBox`implémente le `TextFoundEvent` à cette fin, qui requiert un délégué.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 À l’aide de la `TextFoundEventHandler` déléguer, `FindDialogBox` implémente le `TextFoundEvent`.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind2)]  
  
 Par conséquent, `Find` peut déclencher l’événement lorsqu’un résultat de recherche est trouvé.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind2)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind3)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind3)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind4)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind4)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind5)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind5)]  
  
 La fenêtre propriétaire doit ensuite s’inscrire pour cet événement et le gérer.  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a>Fermeture d’une boîte de dialogue non modale  
 Étant donné que <xref:System.Windows.Window.DialogResult%2A> n’avez pas besoin d’être défini, une boîte de dialogue non modale peut être fermé à l’aide du système fournissent des mécanismes, notamment les suivantes :  
  
-   En cliquant sur le **fermer** bouton dans la barre de titre.  
  
-   en appuyant sur Alt+F4 ;  
  
-   En choisissant **fermer** à partir de la **système** menu.  
  
 Votre code peut aussi appeler <xref:System.Windows.Window.Close%2A> lors de la **fermer** du bouton.  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de Popup](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [Exemple de boîte de dialogue](http://go.microsoft.com/fwlink/?LinkID=159984)  
 [Exemple de contrôle personnalisé ColorPicker](http://go.microsoft.com/fwlink/?LinkID=159977)
