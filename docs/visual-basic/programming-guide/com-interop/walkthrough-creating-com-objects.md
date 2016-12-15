---
title: "Walkthrough: Creating COM Objects with Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "COM interop, creating COM objects"
  - "COM objects, creating"
  - "COM interop, walkthroughs"
  - "object creation, COM objects"
  - "COM objects, walkthroughs"
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Creating COM Objects with Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lors de la création de nouvelles applications ou de nouveaux composants, il est conseillé de créer des assemblys .NET Framework.  Toutefois, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] facilite également l'exposition d'un composant .NET Framework à COM.  Cela vous permet de fournir de nouveaux composants pour des suites d'applications antérieures qui requièrent des composants COM.  Cette procédure pas à pas montre comment utiliser [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour exposer des objets [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] en tant qu'objets COM, avec et sans le modèle de classe COM.  
  
 La façon la plus simple d'exposer des objets COM consiste à utiliser le modèle de classe COM.  Ce modèle crée une classe, puis configure votre projet de façon à générer la couche classe et interopérabilité en tant qu'objet COM et l'inscrire auprès du système d'exploitation.  
  
> [!NOTE]
>  Bien que vous puissiez également exposer une classe créée dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] en tant qu'objet COM pour le code non managé à utiliser, il ne s'agit pas d'un véritable objet COM et il ne peut pas être utilisé par [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Pour plus d'informations, consultez [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Pour créer un objet COM à l'aide du modèle de classe COM  
  
1.  Ouvrez un nouveau projet d'application Windows à partir du menu **Fichier** en cliquant sur **Nouveau projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet** sous le champ **Types de projets**, assurez\-vous que Windows est sélectionné.  Sélectionnez **Bibliothèque de classes** dans la liste **Modèles**, puis cliquez sur **OK**.  Le nouveau projet s'affiche.  
  
3.  Sélectionnez **Ajouter un nouvel élément** dans le menu **Projet**.  La boîte de dialogue **Ajouter un nouvel élément** s'affiche.  
  
4.  Sélectionnez **Classe COM** dans la liste **Modèles**, puis cliquez sur **Ajouter**.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ajoute une nouvelle classe et configure le nouveau projet pour COM Interop.  
  
5.  Ajoutez du code, par exemple des propriétés, méthodes et événements, à la classe COM.  
  
6.  Sélectionnez **Générer ClassLibrary1** dans le menu **Générer**.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] génère l'assembly et inscrit l'objet COM auprès du système d'exploitation.  
  
## Création d'objets COM sans le modèle de classe COM  
 Vous pouvez également créer une classe COM manuellement au lieu d'utiliser le modèle de classe COM.  Cette procédure est utile lorsque vous travaillez à partir de la ligne de commande ou lorsque vous souhaitez davantage de contrôle sur le mode de définition des objets COM.  
  
#### Pour configurer votre projet pour générer un objet COM  
  
1.  Ouvrez un nouveau projet d'application Windows à partir du menu **Fichier** en cliquant sur **Nouveau Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet** sous le champ **Types de projets**, assurez\-vous que Windows est sélectionné.  Sélectionnez **Bibliothèque de classes** dans la liste **Modèles**, puis cliquez sur **OK**.  Le nouveau projet s'affiche.  
  
3.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.  Le **Concepteur de projets** s'affiche.  
  
4.  Cliquez sur l'onglet **Compiler**.  
  
5.  Activez la case à cocher **Inscrire pour COM Interop**.  
  
#### Pour configurer le code de votre classe pour créer un objet COM  
  
1.  ‎Dans l'**Explorateur de solutions**, double\-cliquez sur **Class1.vb** pour afficher son code.  
  
2.  Renommez la classe `ComClass1`.  
  
3.  Ajoutez les constantes suivantes à `ComClass1`.  Elles stockeront les constantes GUID \(identificateur global unique\) dont les objets COM doivent être assortis.  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  Dans le menu **Outils**, cliquez sur **Create GUID**.  Dans la boîte de dialogue **Create GUID**, cliquez sur **Format du Registre**, puis sur **Copier**.  Cliquez sur **Quitter**.  
  
5.  Remplacez la chaîne vide de `ClassId` par le GUID et supprimez les accolades de début et de fin.  Par exemple, si le GUID fourni par Guidgen est `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`, votre code doit s'afficher comme suit :  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  Répétez les étapes précédentes pour les constantes `InterfaceId` et `EventsId`, comme dans l'exemple suivant.  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  Assurez\-vous que les GUID sont nouveaux et uniques, faute de quoi votre composant COM pourrait présenter des conflits avec d'autres composants COM.  
  
7.  Ajoutez l'attribut `ComClass` à `ComClass1`, en indiquant les GUID de l'ID de la classe, de l'interface et des événements, comme dans l'exemple suivant :  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  Les classes COM doivent avoir un constructeur `Public Sub New()` sans paramètre, sans quoi elles ne seront pas inscrites correctement.  Ajoutez un constructeur sans paramètre à la classe :  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. Ajoutez des propriétés, méthodes et événements à la classe, en la terminant par une instruction `End Class`.  Sélectionnez **Générer la solution** dans le menu **Générer**.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] génère l'assembly et inscrit l'objet COM auprès du système d'exploitation.  
  
    > [!NOTE]
    >  Les objets COM que vous générez avec [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peuvent pas être utilisés par d'autres applications [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], car ils ne constituent pas de véritables objets COM.  Les tentatives d'ajout de références à ces objets COM généreront une erreur.  Pour plus d'informations, consultez [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md)   
 [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)