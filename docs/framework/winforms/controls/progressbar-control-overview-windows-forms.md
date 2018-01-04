---
title: "Vue d'ensemble du contrôle ProgressBar (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c5ca5fd908124b0f38643c7b2833ba591be3b980
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="progressbar-control-overview-windows-forms"></a>Vue d'ensemble du contrôle ProgressBar (Windows Forms)
> [!IMPORTANT]
>  Le contrôle <xref:System.Windows.Forms.ToolStripProgressBar> remplace le contrôle <xref:System.Windows.Forms.ProgressBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ProgressBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Windows Forms <xref:System.Windows.Forms.ProgressBar> contrôle indique la progression d’un processus en affichant un nombre approprié de rectangles disposés dans une barre horizontale. Lorsque le processus est terminé, la barre est remplie. Barres de progression sont couramment utilisées pour permettre à l’utilisateur une idée de la manière attendre un processus s’achève ; par exemple, quand un fichier volumineux est chargé.  
  
> [!NOTE]
>  Le <xref:System.Windows.Forms.ProgressBar> contrôle peut uniquement être orienté horizontalement sur le formulaire.  
  
## <a name="key-properties-and-methods"></a>Méthodes et propriétés de clé  
 Les propriétés de clé de la <xref:System.Windows.Forms.ProgressBar> contrôle sont <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>, et <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. Le <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> propriétés définissent les valeurs maximales et minimales que la barre de progression peut afficher. Le <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété représente la progression a été effectuée vers la réalisation de l’opération. Étant donné que la barre s’affichée dans le contrôle est constituée de blocs, la valeur affichée par le <xref:System.Windows.Forms.ProgressBar> contrôle est seulement une approximation du <xref:System.Windows.Forms.ProgressBar.Value%2A> valeur actuelle de la propriété. Selon la taille de la <xref:System.Windows.Forms.ProgressBar> (contrôle), le <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété détermine à quel moment afficher le bloc suivant.  
  
 La méthode la plus courante pour mettre à jour la valeur de progression actuelle consiste à écrire du code pour définir le <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété. Dans l’exemple de chargement d’un fichier volumineux, vous pouvez définir la valeur maximale pour la taille du fichier en kilo-octets. Par exemple, si le <xref:System.Windows.Forms.ProgressBar.Maximum%2A> est définie sur 100, le <xref:System.Windows.Forms.ProgressBar.Minimum%2A> est définie sur 10 et le <xref:System.Windows.Forms.ProgressBar.Value%2A> est définie à 50, 5 rectangles seront affichés. Il s’agit de la moitié du nombre qui peut être affiché.  
  
 Toutefois, il existe des autres moyens de modifier la valeur affichée par le <xref:System.Windows.Forms.ProgressBar> (contrôle), à l’exception de paramètre le <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété directement. Le <xref:System.Windows.Forms.ProgressBar.Step%2A> propriété peut être utilisée pour spécifier une valeur à incrémenter le <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété par. Ensuite, l’appel du <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> méthode incrémente la valeur. Pour faire varier la valeur d’incrément, vous pouvez utiliser la <xref:System.Windows.Forms.ProgressBar.Increment%2A> (méthode) et spécifiez une valeur d’incrémentation le <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété.  
  
 Un autre contrôle graphique qui informe l’utilisateur sur l’action en cours est le <xref:System.Windows.Forms.StatusBar> contrôle.  
  
> [!IMPORTANT]
>  Le <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> contrôles remplacer et ajouter des fonctionnalités à la <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> contrôle ; Toutefois, le <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> contrôles sont conservés pour la compatibilité descendante et l’utilisation future si vous Choisissez.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ProgressBar>  
 [ProgressBar, contrôle](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
