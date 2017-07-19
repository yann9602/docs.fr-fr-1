---
title: "D&#233;buter avec l&#39;encre | Microsoft Docs"
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
  - "animation, couleurs du pinceau dégradé"
  - "pinceaux, animer les couleurs de"
  - "pinceau dégradé, animer les couleurs de"
  - "code procédural à la place de XAML"
  - "XAML, code procédural à la place de"
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# D&#233;buter avec l&#39;encre
Incorporer de l'encre numérique à vos applications est désormais plus facile que jamais.  L'encre a évolué ; après avoir été corollaire de la méthode de programmation de COM et de Windows Forms, elle est désormais totalement intégrée à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Vous n'avez pas besoin d'installer de Kits de développement logiciel \(SDK\) séparés ou de bibliothèques Runtime.  
  
## Composants requis  
 Pour utiliser les exemples suivants, vous devez tout d'abord installer Microsoft Visual Studio 2005 et le [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].  Vous devez également comprendre comment écrire des applications pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Pour plus d'informations sur la mise en route de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## Démarrage rapide  
 Cette section vous aide à écrire une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simple pour collecter de l'encre.  
  
 Si vous ne l'avez pas encore fait, installez Microsoft Visual Studio 2005 et le [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)].  En général, avant de pouvoir faire fonctionner les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il faut qu'elles soient compilées, même si elles sont entièrement composées de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Toutefois, le [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] inclut une application \(XAMLPad\) conçue pour accélérer le processus d'implémentation d'une interface utilisateur basée sur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Vous pouvez utiliser cette application pour afficher et vous entraîner avec les premiers exemples de ce document.  Le processus de création d'applications compilées avec [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est expliqué plus loin dans ce document.  
  
 Pour lancer XAMLPad, cliquez sur le menu **Démarrer**, pointez sur **Tous les programmes**, sur **Kit de développement logiciel Microsoft Windows**, sur **Outils**, puis cliquez sur **XAMLPad**.  Dans le volet de rendu, XAMLPad restitue le code XAML entré dans le volet de code.  Lorsque vous modifiez le code XAML, les modifications apparaissent immédiatement dans le volet de rendu.  
  
#### Vous avez de l'encre ?  
 Pour démarrer votre première application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prenant en charge l'encre :  
  
1.  Ouvrez Microsoft Visual Studio 2005.  
  
2.  Créez une nouvelle **Application Windows \(WPF\)**.  
  
3.  Tapez `<InkCanvas/>` entre les balises `<Grid>`.  
  
4.  Appuyez sur **F5** pour lancer votre application dans le débogueur.  
  
5.  À l'aide d'un stylet ou d'une souris, écrivez hello world dans la fenêtre.  
  
 Vous avez écrit l'équivalent d'une application « hello world » à l'encre avec 12 séquences de touches seulement \!  
  
#### Comment enrichir votre application  
 Tirez parti de certaines fonctionnalités du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Remplacez tout ce qui se trouve entre les balises \<Window\> \(ouverture\) et \<\/Window\> \(fermeture\) par le balisage suivant afin d'obtenir un arrière\-plan au pinceau à dégradé sur votre surface d'encrage.  
  
 [!code-xml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### Utilisation d'animations  
 Pour vous amuser, animez les couleurs du pinceau à dégradé.  Ajoutez le code [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] suivant après la balise de fermeture `</InkCanvas>` mais avant la balise de fermeture `</Page>`.  
  
 [!code-xml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### Ajout de code après XAML  
 Tandis que XAML facilite la conception de l'interface utilisateur, toutes les applications réelles doivent ajouter du code pour gérer des événements.  Voici un exemple simple effectuant un zoom sur l'encre en réponse à un clic avec le bouton droit de la souris :  
  
 Définissez le gestionnaire `MouseRightButtonUp` dans votre code [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] :  
  
 [!code-xml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 Dans l'Explorateur de solutions de Visual Studio, développez Windows1.xaml et ouvrez le fichier code\-behind, Window1.xaml.cs ou Window1.xaml.vb si vous utilisez Visual Basic.  Ajoutez le code du gestionnaire d'événements suivant :  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 Vous pouvez alors exécuter votre application.  Ajoutez de l'encre, puis cliquez avec le bouton droit de la souris ou effectuez l'opération équivalente en appuyant sur le stylet et en le maintenant enfoncé.  
  
#### Utilisation du code procédural au lieu du code XAML  
 Vous pouvez accéder à toutes les fonctionnalités [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] depuis le code procédural.  Voici une application « Hello Ink World » pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui n'utilise pas du tout de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Collez le code ci\-dessous dans une application console vide de Visual Studio.  Ajoutez des références aux assemblys PresentationCore, PresentationFramework et WindowsBase et générez l'application en appuyant sur **F5** :  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## Voir aussi  
 [Encre numérique](../../../../docs/framework/wpf/advanced/digital-ink.md)   
 [Collecte d'encre](../../../../docs/framework/wpf/advanced/collecting-ink.md)   
 [Reconnaissance d'écriture manuscrite](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)   
 [Stockage de l'encre](../../../../docs/framework/wpf/advanced/storing-ink.md)