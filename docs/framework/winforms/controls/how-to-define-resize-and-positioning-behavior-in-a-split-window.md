---
title: "Comment&#160;: d&#233;finir le redimensionnement et le positionnement du comportement dans une fen&#234;tre fractionn&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "fenêtres fractionnées, redimensionner"
  - "SplitContainer (contrôle Windows Forms), redimensionner"
  - "fenêtres fractionnées, redimensionner"
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: d&#233;finir le redimensionnement et le positionnement du comportement dans une fen&#234;tre fractionn&#233;e
Les panneaux du contrôle <xref:System.Windows.Forms.SplitContainer> se prêtent bien au redimensionnement et à la manipulation par les utilisateurs.  Toutefois, il peut arriver que vous souhaitiez contrôler par programme le séparateur, sa position et à quel degré il peut être déplacé.  
  
 La propriété <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> et les autres propriétés du contrôle <xref:System.Windows.Forms.SplitContainer> vous offrent un contrôle précis sur le comportement de votre interface utilisateur pour l'adapter à vos besoins.  Ces propriétés sont répertoriées dans le tableau suivant.  
  
|Nom|Description|  
|---------|-----------------|  
|Propriété <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>|Détermine si le séparateur peut être déplacé au moyen du clavier ou de la souris.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>|Détermine la distance en pixels entre le bord gauche ou supérieur et la barre de fractionnement mobile.|  
|Propriété <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>|Détermine la distance minimale, en pixels, que l'utilisateur peut faire parcourir au séparateur.|  
  
 L'exemple suivant modifie la propriété <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> pour créer l'effet d'un « séparateur d'alignement » ; lorsque l'utilisateur fait glisser le séparateur, il incrémente par unités de 10 pixels plutôt que par la valeur par défaut 1.  
  
### Pour définir le comportement de redimensionnement du contrôle SplitContainer  
  
1.  Dans une procédure, affectez à la propriété <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> la taille voulue, afin que le comportement « d'alignement » du séparateur s'exécute.  
  
     Dans l'exemple de code suivant, dans l'événement <xref:System.Windows.Forms.Form.Load> du formulaire, le séparateur du contrôle <xref:System.Windows.Forms.SplitContainer> est configuré pour un saut de 10 pixels lorsque vous le faites glisser.  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     Le fait de déplacer le séparateur légèrement vers la gauche ou la droite n'aura aucun effet visible ; toutefois, lorsque le pointeur de la souris se déplace de 10 pixels dans l'un des deux sens, le séparateur s'alignera sur la nouvelle position.  
  
## Voir aussi  
 <xref:System.Windows.Forms.SplitContainer>   
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>