---
title: "Vue d&#39;ensemble de la navigation structur&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "navigation structurée (WPF)"
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
caps.latest.revision: 43
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 36
---
# Vue d&#39;ensemble de la navigation structur&#233;e
Le contenu qui peut être hébergé par une [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], un <xref:System.Windows.Controls.Frame> ou un <xref:System.Windows.Navigation.NavigationWindow> est composé de pages pouvant être identifiées par [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] à en\-tête pack et accédées à l'aide de liens hypertexte.  La structure des pages et les méthodes permettant de les parcourir \(définies par des liens hypertexte\) correspondent à la topologie de navigation.  Une topologie est adaptée à divers types d'applications, plus particulièrement celles qui parcourent des documents.  En ce qui concerne ces applications, l'utilisateur peut passer d'une page à l'autre sans qu'il y ait de lien entre ces deux pages.  
  
 Toutefois, d'autres types d'applications comportent des pages qui doivent savoir quand l'utilisateur est passé d'une page à l'autre.  Prenons, par exemple, une application de ressources humaines qui comporte une page répertoriant tous les employés d'une organisation \(la page " Liste des employés "\).  Cette page peut également permettre à l'utilisateur d'ajouter un nouvel employé en cliquant sur un lien hypertexte.  L'utilisateur passe alors à une page " Ajouter un employé ", qui rassemble les détails du nouvel employé, puis revient à la page " Liste des employés " pour créer l'employé et mettre la liste à jour.  Ce style de navigation est semblable à l'appel d'une méthode permettant d'effectuer un traitement et de retourner une valeur \(" programmation structurée "\).  En tant que tel, ce style de navigation est appelé " *navigation structurée* ".  
  
 La classe <xref:System.Windows.Controls.Page> n'implémente pas la prise en charge de la navigation structurée.  En lieu et place, la classe <xref:System.Windows.Navigation.PageFunction%601> est dérivée de <xref:System.Windows.Controls.Page> et l'étend avec les constructions de base requises pour la navigation structurée.  Cette rubrique explique comment définir une navigation structurée à l'aide de <xref:System.Windows.Navigation.PageFunction%601>.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Structured_Navigation"></a>   
## Navigation structurée  
 Lorsqu'une page en appelle une autre dans une navigation structurée, une partie ou l'ensemble des comportements suivants sont requis :  
  
-   La page appelante accède à la page appelée et passe éventuellement les paramètres requis par la page appelée.  
  
-   Lorsque l'utilisateur a terminé d'utiliser la page appelante, la page appelée revient à la page appelante et, éventuellement :  
  
    -   Retourne les informations d'état qui décrivent comment l'utilisateur a quitté la page appelante \(par exemple, en appuyant sur un bouton OK ou Annuler\).  
  
    -   Retourne les données recueillies par l'utilisateur \(par exemple, détails d'un nouvel employé\).  
  
-   Lorsque la page appelante revient à la page appelée, celle\-ci est supprimée de l'historique de navigation afin d'isoler les différentes instances d'une page appelée.  
  
 Ces comportements sont illustrés par la figure suivante.  
  
 ![Flux entre la page appelante et la page appelée](../../../../docs/framework/wpf/app-development/media/structurednavigationoverviewfigure1.png "StructuredNavigationOverviewFigure1")  
  
 Vous pouvez implémenter ces comportements en utilisant un <xref:System.Windows.Navigation.PageFunction%601> comme page appelée.  
  
<a name="Structured_Navigation_with_PageFunction"></a>   
## Navigation structurée avec PageFunction  
 Cette rubrique indique comment implémenter les mécanismes de base de la navigation structurée avec un seul <xref:System.Windows.Navigation.PageFunction%601>.  Dans cet exemple, un <xref:System.Windows.Controls.Page> appelle un <xref:System.Windows.Navigation.PageFunction%601> pour obtenir et retourner une valeur <xref:System.String> fournie par l'utilisateur.  
  
### Création d'une page appelante  
 La page qui appelle un <xref:System.Windows.Navigation.PageFunction%601> peut être <xref:System.Windows.Controls.Page> ou <xref:System.Windows.Navigation.PageFunction%601>.  Dans cet exemple, il s'agit de <xref:System.Windows.Controls.Page>, comme indiqué dans le code suivant.  
  
 [!code-xml[StructuredNavigationSample#CallingPageDefaultMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]  
[!code-xml[StructuredNavigationSample#CallingPageDefaultMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]  
  
 [!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
 [!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]  
  
### Création d'une fonction de page à appeler  
 La page appelante pouvant utiliser la page appelée pour recueillir et retourner des données fournies par l'utilisateur, <xref:System.Windows.Navigation.PageFunction%601> est implémenté comme classe générique dont l'argument de type détermine le type de la valeur retournée par la page appelée.  Le code suivant indique l'implémentation initiale de la page appelée à l'aide d'un <xref:System.Windows.Navigation.PageFunction%601> qui retourne <xref:System.String>.  
  
 [!code-xml[StructuredNavigationSample#CalledPageFunctionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]  
  
 [!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
 [!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]  
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]  
  
 La déclaration d'un <xref:System.Windows.Navigation.PageFunction%601> est semblable à celle d'un <xref:System.Windows.Controls.Page> avec ajout des arguments de type.  Comme vous pouvez le constater dans l'exemple de code, les arguments de type sont spécifiés dans une balise [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], à l'aide de l'attribut `x:TypeArguments`, et dans un code\-behind, à l'aide de la syntaxe d'argument de type générique standard.  
  
 Vous ne devez pas utiliser uniquement des classes [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] comme arguments de type.  Un <xref:System.Windows.Navigation.PageFunction%601> peut être appelé pour rassembler des données spécifiques du domaine qui sont abstraites en tant que type personnalisé.  Le code suivant indique comment utiliser un type personnalisé en tant qu'argument de type pour <xref:System.Windows.Navigation.PageFunction%601>.  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]  
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]  
  
 [!code-xml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]  
[!code-xml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]  
  
  
 Les arguments de type pour <xref:System.Windows.Navigation.PageFunction%601> fournissent la fondation pour la communication entre une page appelante et la page appelée, abordée dans les sections suivantes.  
  
 Comme vous le constaterez, le type identifié par la déclaration d'un <xref:System.Windows.Navigation.PageFunction%601> joue un rôle important pour retourner des données d'un <xref:System.Windows.Navigation.PageFunction%601> à la page appelante.  
  
### Appel de PageFunction et passage de paramètres  
 Pour appeler une page, la page appelante doit instancier la page appelée et y accéder à l'aide de la méthode <xref:System.Windows.Navigation.NavigationService.Navigate%2A>.  La page appelante peut ainsi passer les données initiales à la page appelée, comme les valeurs par défaut des données recueillies par la page appelée.  
  
 Le code suivant affiche la page appelée avec un constructeur non défini par défaut permettant d'accepter les paramètres de la page appelante.  
  
 [!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
 [!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]  
  
 Le code suivant affiche la page appelante qui gère l'événement <xref:System.Windows.Documents.Hyperlink.Click> du <xref:System.Windows.Documents.Hyperlink> pour instancier la page appelée et lui passer une valeur de chaîne initiale.  
  
 [!code-xml[StructuredNavigationSample#PassingDataMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]  
  
 Vous n'êtes pas obligé de passer des paramètres à la page appelée.  Vous pouvez plutôt effectuer les opérations suivantes :  
  
-   À partir de la page appelante :  
  
    1.  Instancier le <xref:System.Windows.Navigation.PageFunction%601> appelé à l'aide du constructeur par défaut.  
  
    2.  Stocker les paramètres dans <xref:System.Windows.Application.Properties%2A>.  
  
    3.  Naviguer jusqu'au <xref:System.Windows.Navigation.PageFunction%601> appelé.  
  
-   À partir du <xref:System.Windows.Navigation.PageFunction%601> appelé :  
  
    -   Récupérer et utiliser les paramètres stockés dans <xref:System.Windows.Application.Properties%2A>.  
  
 Cependant, comme vous le constaterez bientôt, vous devez toujours utiliser du code pour instancier la page appelée et pour y accéder afin de recueillir les données retournées par la page appelée.  Pour cette raison, <xref:System.Windows.Navigation.PageFunction%601> doit rester actif, sinon, la prochaine fois que vous accédez à <xref:System.Windows.Navigation.PageFunction%601>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] instancie <xref:System.Windows.Navigation.PageFunction%601> à l'aide du constructeur par défaut.  
  
 Toutefois, pour que la page appelée puisse être retournée, elle doit d'abord retourner des données qui peuvent être récupérées par la page appelante.  
  
### Retour de résultats et de données de tâche à partir d'une tâche vers une page appelante  
 Une fois que l'utilisateur a terminé d'utiliser la page appelée \(opération indiquée dans cet exemple par l'activation du bouton OK ou Annuler\), celle\-ci doit être retournée.  Comme la page appelante a utilisé la page appelée pour recueillir les données de l'utilisateur, elle nécessite deux types d'informations :  
  
1.  Annulation de la page appelée par l'utilisateur \(en cliquant sur le bouton OK ou Annuler, dans cet exemple\).  La page appelante peut ainsi déterminer si les données qu'elle a recueillies auprès de l'utilisateur doivent être traitées.  
  
2.  Données fournies par l'utilisateur.  
  
 Pour retourner des informations, <xref:System.Windows.Navigation.PageFunction%601> implémente la méthode <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>.  Le code suivant indique comment l'appeler.  
  
 [!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
 [!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]  
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]  
  
 Dans cet exemple, si l'utilisateur clique sur le bouton Annuler, la valeur `null` est retournée à la page appelante.  Si vous appuyez sur le bouton OK à la place, la valeur de chaîne fournie par l'utilisateur est retournée.  <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> est une méthode `protected` `virtual` que vous appelez pour retourner vos données à la page appelante.  Les données doivent être empaquetées dans une instance du type générique <xref:System.Windows.Navigation.ReturnEventArgs%601>, dont l'argument de type spécifie le type de valeur retournée par <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A>.  De cette manière, lorsque vous déclarez <xref:System.Windows.Navigation.PageFunction%601> avec un argument de type particulier, vous indiquez que <xref:System.Windows.Navigation.PageFunction%601> retourne une instance du type spécifié par l'argument de type.  Dans cet exemple, l'argument de type et, par conséquent, la valeur de retour sont du type <xref:System.String>.  
  
 Lorsque <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> est appelé, la page appelante doit pouvoir recevoir la valeur de retour de <xref:System.Windows.Navigation.PageFunction%601>.  Pour cette raison, <xref:System.Windows.Navigation.PageFunction%601> implémente l'événement <xref:System.Windows.Navigation.PageFunction%601.Return> que les pages appelantes peuvent gérer.  Lorsque <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> est appelé, <xref:System.Windows.Navigation.PageFunction%601.Return> est déclenché, ce qui permet à la page appelante de s'inscrire avec <xref:System.Windows.Navigation.PageFunction%601.Return> pour recevoir la notification.  
  
 [!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
 [!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]  
  
### Suppression de pages de tâche lorsqu'une tâche est terminée  
 Lorsqu'une page appelée est retournée, si l'utilisateur n'a pas annulé la page appelée, la page appelante traite les données fournies par l'utilisateur et retournées par la page appelée.  En règle générale, ce type d'acquisition de données est une opération isolée. Lorsque la page appelée est retournée, la page appelante doit créer une autre page appelante et y accéder pour capturer davantage de données.  
  
 Toutefois, un utilisateur peut revenir à une instance précédente de la page appelante, sauf si une page appelée est supprimée du [journal](GTMT).  La propriété <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> détermine si un <xref:System.Windows.Navigation.PageFunction%601> est conservé dans le [journal](GTMT).  Par défaut, une fonction de page est automatiquement supprimée lorsque <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> est appelé, car <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> a la valeur `true`.  Pour conserver une fonction de page dans l'historique de navigation après l'appel de <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>, définissez <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> sur la valeur `false`.  
  
<a name="Other_Types_of_Structured_Navigation"></a>   
## Autres types de navigation structurée  
 Cette rubrique illustre l'utilisation la plus élémentaire de <xref:System.Windows.Navigation.PageFunction%601> pour assurer la prise en charge de la navigation structurée par appel\/retour.  Cette base vous permet de créer des types de navigation structurée plus complexes.  
  
 Par exemple, plusieurs pages sont parfois requises par une page appelante afin de rassembler un volume de données suffisant d'un utilisateur ou d'effectuer une tâche.  L'utilisation de plusieurs pages est appelée " Assistant ".  
  
 Dans d'autres cas, une application peut présenter une topologie de navigation complexe qui nécessite une navigation structurée pour pouvoir fonctionner de manière optimale.  Pour plus d'informations, consultez [Vue d'ensemble des topologies de navigation](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Navigation.PageFunction%601>   
 <xref:System.Windows.Navigation.NavigationService>   
 [Vue d'ensemble des topologies de navigation](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)