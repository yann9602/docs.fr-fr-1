---
title: "Comment : définir l'ordre de tabulation dans les Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d514b20381b44102076c776d12181df3838e4eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Comment : définir l'ordre de tabulation dans les Windows Forms
L’ordre de tabulation est l’ordre dans lequel un utilisateur déplace le focus d’un contrôle à un autre en appuyant sur la touche TAB. Chaque formulaire possède son propre ordre de tabulation. Par défaut, l’ordre de tabulation est identique à l’ordre dans lequel vous avez créé les contrôles. Ordre de tabulation de numérotation commence à zéro.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-tab-order-of-a-control"></a>Pour définir l’ordre de tabulation d’un contrôle  
  
1.  Sur le **vue** menu, cliquez sur **l’ordre de tabulation**.  
  
     Cela permet d’activer le mode de sélection d’ordre de tabulation dans le formulaire. Un nombre (représentant le <xref:System.Windows.Forms.Control.TabIndex%2A> propriété) apparaît dans le coin supérieur gauche de chaque contrôle.  
  
2.  Cliquez sur les contrôles de manière séquentielle pour établir l’ordre de tabulation.  
  
    > [!NOTE]
    >  Place d’un contrôle dans l’ordre de tabulation peut être définie à n’importe quelle valeur supérieure ou égale à 0. Lorsque les doublons se produisent, l’ordre de plan des deux contrôles est évalué et le contrôle supérieur est avec onglets en premier. (L’ordre de plan est la superposition visuelle des contrôles d’un formulaire sur l’axe z [profondeur]. L’ordre de plan détermine les contrôles qui sont devant les autres contrôles.) Pour plus d’informations sur l’ordre de plan, consultez [superposition d’objets dans les Windows Forms](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
3.  Lorsque vous avez terminé, cliquez sur **l’ordre de tabulation** sur la **vue** menu pour quitter le mode d’ordre de tabulation.  
  
    > [!NOTE]
    >  Les contrôles qui ne peut pas recevoir le focus, ainsi que les contrôles désactivés et invisibles, n’ont pas un <xref:System.Windows.Forms.Control.TabIndex%2A> propriété et sont pas inclus dans l’ordre de tabulation. Comme un utilisateur appuie sur la touche TAB, ces contrôles sont ignorés.  
  
 Ou bien, l’ordre de tabulation peut être défini dans la fenêtre Propriétés à l’aide du <xref:System.Windows.Forms.Control.TabIndex%2A> propriété. Le <xref:System.Windows.Forms.Control.TabIndex%2A> propriété d’un contrôle détermine où il est positionné dans l’ordre de tabulation. Par défaut, le premier contrôle a un <xref:System.Windows.Forms.Control.TabIndex%2A> valeur 0, la seconde a une <xref:System.Windows.Forms.Control.TabIndex%2A> de 1 et ainsi de suite.  
  
 En outre, par défaut, un <xref:System.Windows.Forms.GroupBox> contrôle possède son propre <xref:System.Windows.Forms.Control.TabIndex%2A> valeur, qui est un nombre entier. A <xref:System.Windows.Forms.GroupBox> contrôle lui-même ne peut pas avoir le focus au moment de l’exécution. Par conséquent, chaque contrôle dans un <xref:System.Windows.Forms.GroupBox> a son propre décimale <xref:System.Windows.Forms.Control.TabIndex%2A> valeur, en commençant par.0. Naturellement, comme le <xref:System.Windows.Forms.Control.TabIndex%2A> d’un <xref:System.Windows.Forms.GroupBox> contrôle est incrémenté, les contrôles qu’il contient seront incrémentés en conséquence. Si vous avez modifié un <xref:System.Windows.Forms.Control.TabIndex%2A> valeur entre 5 et 6, la <xref:System.Windows.Forms.Control.TabIndex%2A> la valeur du premier contrôle dans son groupe devient automatiquement 6.0 et ainsi de suite.  
  
 Enfin, n’importe quel contrôle des nombreuses sur votre formulaire peut être ignoré dans l’ordre de tabulation. En règle générale, appuyez sur TAB successivement au moment de l’exécution sélectionne chaque contrôle dans l’ordre de tabulation. En désactivant le <xref:System.Windows.Forms.Control.TabStop%2A> propriété, vous pouvez faire un contrôle est transféré dans l’ordre de tabulation du formulaire.  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>Pour supprimer un contrôle de l’ordre de tabulation  
  
1.  Valeur du contrôle <xref:System.Windows.Forms.Control.TabStop%2A> propriété `false` dans la fenêtre Propriétés.  
  
     Un contrôle dont <xref:System.Windows.Forms.Control.TabStop%2A> propriété a été définie `false` conserve sa position dans l’ordre de tabulation, même si le contrôle est ignoré lorsque vous faites défiler les contrôles avec la touche TAB.  
  
    > [!NOTE]
    >  Un groupe de cases d’option comporte un seul onglet arrêter au moment de l’exécution. Le bouton sélectionné (autrement dit, le bouton avec son <xref:System.Windows.Forms.RadioButton.Checked%2A> propriété la valeur `true`) a son <xref:System.Windows.Forms.Control.TabStop%2A> propriété automatiquement la valeur `true`, tandis que les autres boutons ont leur <xref:System.Windows.Forms.Control.TabStop%2A> propriété la valeur `false`. Pour plus d’informations sur le regroupement <xref:System.Windows.Forms.RadioButton> contrôles, consultez [regroupement Windows Forms contrôles RadioButton en tant qu’ensemble](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
