---
title: "Procédure pas à pas : Création d’objets COM avec Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- COM interop, creating COM objects
- COM objects, creating
- COM interop, walkthroughs
- object creation, COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cce28e2be5914880107334bf2c4dc4dc645b4793
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Procédure pas à pas : création d'objets COM avec Visual Basic
Lors de la création de nouvelles applications ou composants, il est préférable de créer des assemblys .NET Framework. Toutefois, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] facilite également l’exposition d’un composant .NET Framework à COM. Cela vous permet de fournir de nouveaux composants pour des suites d’applications antérieures qui requièrent des composants COM.. Cette procédure pas à pas montre comment utiliser [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour exposer [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] objets en tant qu’objets COM, avec et sans le modèle de classe COM.  
  
 Pour exposer des objets COM, le plus simple consiste à l’aide de ce modèle. Le modèle de classe COM crée une nouvelle classe, puis configure votre projet pour générer la couche classe et interopérabilité sous la forme d’un objet COM et l’inscrire auprès du système d’exploitation.  
  
> [!NOTE]
>  Bien que vous pouvez également exposer une classe créée dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] en tant qu’objet COM pour le code non managé à utiliser, il n’est pas un véritable objet COM et ne peut pas être utilisé par [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Pour créer un objet COM à l’aide du modèle de classe COM  
  
1.  Ouvrez un nouveau projet d’Application Windows à partir de la **fichier** en cliquant sur **nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue sous la **Types de projet** champ, vérifiez que Windows est sélectionné. Sélectionnez **bibliothèque de classes** à partir de la **modèles** liste, puis cliquez sur **OK**. Le nouveau projet s’affiche.  
  
3.  Sélectionnez **ajouter un nouvel élément** à partir de la **projet** menu. Le **ajouter un nouvel élément** boîte de dialogue s’affiche.  
  
4.  Sélectionnez **classe COM** à partir de la **modèles** liste, puis cliquez sur **ajouter**. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Ajoute une nouvelle classe et configure le nouveau projet pour COM interop.  
  
5.  Ajoutez à la classe COM code tels que les propriétés, méthodes et événements.  
  
6.  Sélectionnez **générer ClassLibrary1** à partir de la **Build** menu. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]génère l’assembly et inscrit l’objet COM avec le système d’exploitation.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Création d’objets COM sans le modèle de classe COM  
 Vous pouvez également créer une classe COM manuellement au lieu d’utiliser le modèle de classe com.. Cette procédure est utile lorsque vous travaillez à partir de la ligne de commande ou lorsque vous souhaitez mieux contrôler la façon dont les objets COM sont définies.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Pour configurer votre projet pour générer un objet COM  
  
1.  Ouvrez un nouveau projet d’Application Windows à partir de la **fichier** en cliquant sur **NewProject**.  
  
2.  Dans le **nouveau projet** boîte de dialogue sous la **Types de projet** champ, vérifiez que Windows est sélectionné. Sélectionnez **bibliothèque de classes** à partir de la **modèles** liste, puis cliquez sur **OK**. Le nouveau projet s’affiche.  
  
3.  Dans **l’Explorateur de solutions**, cliquez sur votre projet, puis cliquez sur **propriétés**. Le **Concepteur de projets** s’affiche.  
  
4.  Cliquez sur l’onglet **Compiler**.  
  
5.  Sélectionnez le **inscrire pour COM Interop** case à cocher.  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Pour définir le code dans votre classe pour créer un objet COM  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur **Class1.vb** pour afficher son code.  
  
2.  Renommez la classe `ComClass1`.  
  
3.  Ajoutez les constantes suivantes à `ComClass1`. Ils stockera les constantes GUID (Globally Unique Identifier) que les objets COM sont tenus d’avoir.  
  
     [!code-vb[VbVbalrInterop n °&2;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  Sur le **outils** menu, cliquez sur **créer un Guid**. Dans le **créer un GUID** boîte de dialogue, cliquez sur **au Format de Registre** , puis **copie**. Cliquez sur **Quitter**.  
  
5.  Remplacez la chaîne vide pour la `ClassId` avec le GUID, accolades suppression de début et de fin. Par exemple, si le GUID fourni par Guidgen est `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , votre code doit apparaître comme suit.  
  
     [!code-vb[VbVbalrInterop n °&3;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  Répétez les étapes précédentes pour le `InterfaceId` et `EventsId` constantes, comme dans l’exemple suivant.  
  
     [!code-vb[VbVbalrInterop n °&4;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  Assurez-vous que les GUID sont nouveaux et uniques ; dans le cas contraire, votre composant COM pourrait être en conflit avec d’autres composants.  
  
7.  Ajouter la `ComClass` l’attribut `ComClass1`, en spécifiant le GUID pour l’ID de classe, les ID d’Interface et les ID d’événements comme dans l’exemple suivant :  
  
     [!code-vb[VbVbalrInterop n °&5;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  Classes COM doivent avoir un sans paramètre `Public Sub New()` constructeur ou la classe n’inscrira pas correctement. Ajoutez un constructeur sans paramètre à la classe :  
  
     [!code-vb[VbVbalrInterop n °&6;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. Ajoutez des propriétés, méthodes et événements à la classe, en terminant par un `End Class` instruction. Sélectionnez **générer la Solution** à partir de la **Build** menu. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]génère l’assembly et inscrit l’objet COM avec le système d’exploitation.  
  
    > [!NOTE]
    >  Les objets COM que vous générez avec [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas être utilisé par d’autres [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] applications car ils ne sont pas des objets COM trues. Tente d’ajouter des références à ces objets COM génère une erreur. Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Procédure pas à pas : Implémentation de l’héritage avec les objets COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Directive #Region](../../../visual-basic/language-reference/directives/region-directive.md)   
 [Interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Dépannage des problèmes liés à l’interopérabilité](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
