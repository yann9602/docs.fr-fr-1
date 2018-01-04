---
title: "Comment : définir le redimensionnement et le positionnement du comportement dans une fenêtre fractionnée"
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
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed78a49119c87c52a07cc2ade030e66087d3f420
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>Comment : définir le redimensionnement et le positionnement du comportement dans une fenêtre fractionnée
Les panneaux de la <xref:System.Windows.Forms.SplitContainer> contrôle se prêtent bien au redimensionnement et manipulées par les utilisateurs. Toutefois, il peut arriver lorsque vous souhaitez contrôler par programme le séparateur, où il est positionné, et dans quelle mesure il peut être déplacé.  
  
 Le <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriété et les autres propriétés sur le <xref:System.Windows.Forms.SplitContainer> contrôle vous donne un contrôle précis sur le comportement de votre interface utilisateur en fonction de vos besoins. Ces propriétés sont répertoriées dans le tableau suivant.  
  
|Name|Description|  
|----------|-----------------|  
|Propriété <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>|Détermine si le séparateur est mobile au moyen de la souris ou du clavier.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>|Détermine la distance en pixels du bord gauche ou supérieur à la barre de fractionnement mobile.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>|Détermine la distance minimale, en pixels, que le séparateur peut être déplacé par l’utilisateur.|  
  
 L’exemple suivant modifie le <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriété pour créer un effet « séparateur d’alignement » ; lorsque l’utilisateur fait glisser le séparateur, il incrémente par unités de 10 pixels plutôt que la valeur par défaut 1.  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>Pour définir le comportement de redimensionnement SplitContainer  
  
1.  Dans une procédure, vous devez définir le <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriété à la taille de votre choix, afin que le comportement « d’alignement » du séparateur s’exécute.  
  
     Dans l’exemple de code suivant, au sein du formulaire <xref:System.Windows.Forms.Form.Load> événement, le séparateur dans le <xref:System.Windows.Forms.SplitContainer> contrôle est défini sur le saut de 10 pixels lorsque vous faites glisser.  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     Déplacer le séparateur légèrement vers la droite ou gauche n’a aucun effet visible ; Toutefois, lorsque le pointeur de souris passe 10 pixels dans les deux sens, le séparateur s’alignera à la nouvelle position.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
