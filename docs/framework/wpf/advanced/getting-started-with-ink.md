---
title: "Débuter avec l'encre"
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
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc8ffe9ad68060d9dfbcafe99133a736237a2bb3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getting-started-with-ink"></a>Débuter avec l'encre
Incorporation d’encre numérique dans vos applications est plus facile que jamais. Encre a évolué d’être un corollaire à la méthode COM et Windows Forms de la programmation à la réalisation d’une intégration complète dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Vous n’avez pas besoin installer les kits de développement logiciel distincts ou des bibliothèques runtime.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour utiliser les exemples suivants, vous devez d’abord installer Microsoft Visual Studio 2005 et le [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Vous devez également comprendre comment écrire des applications pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour plus d’informations sur la prise en main de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [procédure pas à pas : Ma première application de bureau WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="quick-start"></a>Démarrage rapide  
 Cette section vous permet d’écrire un simple [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application qui collecte de l’encre.  
  
 Si vous n’avez pas déjà fait, installez Microsoft Visual Studio 2005 et le [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]applications généralement doivent être compilées avant de pouvoir afficher, même si elles sont entièrement composent de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Toutefois, le [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] inclut une application, XamlPad, conçue pour accélérer le processus d’implémentation d’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-en fonction de l’interface utilisateur. Vous pouvez utiliser cette application pour afficher et vous entraîner avec les premiers exemples dans ce document. Le processus de création d’applications compilées [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est couvert plus loin dans ce document.  
  
 Pour lancer XAMLPad, cliquez sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur **Winndows SDK Microsoft**, pointez sur **outils**, puis cliquez sur **XAMLPad**. Dans le volet de rendu, XAMLPad restitue le code XAML dans le volet du code. Vous pouvez modifier le code XAML, et les modifications apparaissent immédiatement dans le volet de rendu.  
  
#### <a name="got-ink"></a>Vous avez encre ?  
 Pour démarrer votre première [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application qui prend en charge les services d’encre :  
  
1.  Ouvrez Microsoft Visual Studio 2005  
  
2.  Créer un nouveau **Application WPF (Windows)**  
  
3.  Type `<InkCanvas/>` entre les `<Grid>` balises  
  
4.  Appuyez sur **F5** pour lancer votre application dans le débogueur  
  
5.  À l’aide d’un stylet ou une souris, écrire **Bonjour** dans la fenêtre  
  
 Vous avez écrit l’équivalent d’encre d’une application « hello world » avec des séquences de touches que 12 !  
  
#### <a name="spice-up-your-application"></a>Enrichir votre Application  
 Tirez parti de certaines fonctionnalités de le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Remplacez tout le contenu entre l’ouverture \<fenêtre > et la fermeture de \</Window > balises par le balisage suivant pour obtenir un arrière-plan de pinceau de dégradé sur votre surface d’encre.  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a>À l’aide d’Animation  
 Pour vous amuser, animez les couleurs de pinceau de dégradé. Ajoutez le code suivant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] après la fermeture `</InkCanvas>` balise mais avant la fermeture `</Page>` balise.  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a>Ajout de Code après le code XAML  
 Bien que le XAML facilite la conception de l’interface utilisateur, n’importe quelle application réelle doit ajouter du code pour gérer les événements. Voici un exemple simple qui effectue un zoom sur l’encre en réponse à un clic droit de la souris :  
  
 Définir le `MouseRightButtonUp` gestionnaire dans votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 Dans l’Explorateur de solutions de Visual Studio, développez Windows1.xaml et ouvrez le fichier code-behind, Window1.xaml.cs ou Window1.xaml.vb si vous utilisez Visual Basic. Ajoutez le code de gestionnaire d’événements suivantes :  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 Maintenant, exécutez votre application. Ajoutez de l’encre et le bouton droit de la souris ou effectuer un équivalent appuyer et maintenir avec un stylet.  
  
#### <a name="using-procedural-code-instead-of-xaml"></a>À l’aide des procédures de Code au lieu de XAML  
 Vous pouvez accéder à tous les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctionnalités à partir de procédures de code. Voici une application « Hello Ink World » pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui n’utilise aucun [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] du tout. Collez le code ci-dessous dans une Application Console vide dans Visual Studio. Ajouter des références aux assemblys WindowsBase, PresentationCore et PresentationFramework et générez l’application en appuyant sur **F5**:  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Encre numérique](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [Collecte d'encre](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [Reconnaissance d'écriture manuscrite](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [Stockage de l’encre](../../../../docs/framework/wpf/advanced/storing-ink.md)
