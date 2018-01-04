---
title: "Meilleures pratiques pour le contrôle TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f2c5a16ea1f07f7688c9df14bdb6b29350f3acf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>Meilleures pratiques pour le contrôle TableLayoutPanel
Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle fournit des fonctionnalités de disposition puissantes que vous devez examiner soigneusement avant à l’aide de vos Windows Forms.  
  
## <a name="recommendations"></a>Recommandations  
 Les recommandations suivantes vous aideront à utiliser le <xref:System.Windows.Forms.TableLayoutPanel> contrôle mieux.  
  
### <a name="targeted-use"></a>Utilisez ciblé  
 Utilisez le <xref:System.Windows.Forms.TableLayoutPanel> contrôler avec parcimonie. Vous ne devez pas l’utiliser dans toutes les situations qui requièrent une disposition redimensionnable. La liste suivante décrit les dispositions qui bénéficient le plus de l’utilisation de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle :  
  
-   Mises en page dans laquelle il existe plusieurs parties du formulaire, redimensionnement proportionnellement les uns aux autres.  
  
-   Les dispositions qui seront modifiées ou générées dynamiquement au moment de l’exécution, telles que des formulaires de saisie de données qui ont des champs personnalisables par l’utilisateur ajoutée ou soustraite en fonction des préférences.  
  
-   Dispositions qui doivent rester à une taille fixe totale. Par exemple, vous avez peut-être une boîte de dialogue qui doit rester inférieure à 800 x 600, mais vous devez prendre en charge les chaînes localisées.  
  
 La liste suivante décrit les dispositions qui ne bénéficient pas beaucoup d’à l’aide de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle :  
  
-   Formulaires de saisie des données simple avec une seule colonne d’étiquettes et une seule colonne de zones de saisie de texte.  
  
-   Formulaires avec une seule grande zone d’affichage qui doit remplir tout l’espace disponible lorsqu’un redimensionnement se produit. Un exemple est un formulaire qui affiche un seul <xref:System.Windows.Forms.PropertyGrid> contrôle. Dans ce cas, utilisez l’ancrage, étant donné que rien d’autre ne doit se développer lorsque le formulaire est redimensionné.  
  
 Choisissez avec soin les contrôles qui doivent se trouver dans un <xref:System.Windows.Forms.TableLayoutPanel> contrôle. Si vous disposez d’espace pour votre texte augmente de 30 % à l’aide d’ancrage, envisagez d’utiliser le <xref:System.Windows.Forms.Control.Anchor%2A> propriété uniquement. Si vous pouvez estimer l’espace requis par votre disposition, l’utilisation du <xref:System.Windows.Forms.Control.Dock%2A> et <xref:System.Windows.Forms.Control.Anchor%2A> est plus facile que d’estimer les détails de l’espace restant et <xref:System.Windows.Forms.Control.AutoSize%2A> comportement.  
  
 En général, lorsque vous concevez votre disposition avec la <xref:System.Windows.Forms.TableLayoutPanel> contrôler, de simplifier la conception.  
  
### <a name="use-the-document-outline-window"></a>Utilisez la fenêtre Structure du Document  
 La fenêtre Structure du Document vous donne une vue d’arborescence de votre disposition, vous pouvez utiliser pour manipuler les relations parent-enfant et de z de vos contrôles. À partir de la **menu Affichage**, sélectionnez **autres fenêtres**, puis sélectionnez **structure du Document**.  
  
### <a name="avoid-nesting"></a>Évitez l’imbrication  
 Évitez d’imbriquer d’autres <xref:System.Windows.Forms.TableLayoutPanel> des contrôles dans un <xref:System.Windows.Forms.TableLayoutPanel> contrôle. Débogage des dispositions imbriquées peut être difficile.  
  
### <a name="avoid-visual-inheritance"></a>Évitez l’héritage visuel  
 Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle ne prend pas en charge l’héritage visuel dans le Concepteur Windows Forms. A <xref:System.Windows.Forms.TableLayoutPanel> contrôle dans une classe dérivée apparaît comme « verrouillé » au moment du design.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
