---
title: "Procédure pas à pas : création d'objets COM avec Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff7d3868a2e3ddaba06ebc6f98c8eacfc7299366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Procédure pas à pas : création d'objets COM avec Visual Basic
Lors de la création de nouvelles applications ou des composants, il est préférable de créer des assemblys .NET Framework. Toutefois, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] facilite également l’exposition d’un composant .NET Framework à COM. Cela vous permet de fournir de nouveaux composants pour des suites d’applications antérieures qui requièrent des composants COM. Cette procédure pas à pas montre comment utiliser [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour exposer [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objets en tant qu’objets COM, avec et sans le modèle de classe COM.  
  
 Pour exposer des objets COM, le plus simple consiste à l’aide du modèle de classe COM. Le modèle de classe COM crée une nouvelle classe, puis configure votre projet pour générer la couche classe et interopérabilité sous la forme d’un objet COM et l’inscrire auprès du système d’exploitation.  
  
> [!NOTE]
>  Bien que vous pouvez également exposer une classe créée dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] comme un objet COM pour le code non managé à utiliser, il n’est pas un objet COM réel et ne peut pas être utilisé par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Pour créer un objet COM à l’aide du modèle de classe COM  
  
1.  Ouvrez un nouveau projet d’Application Windows à partir de la **fichier** en cliquant sur **nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue sous le **Types de projets** champ, vérifiez que Windows est sélectionné. Sélectionnez **bibliothèque de classes** à partir de la **modèles** liste, puis cliquez sur **OK**. Le nouveau projet s’affiche.  
  
3.  Sélectionnez **ajouter un nouvel élément** à partir de la **projet** menu. La boîte de dialogue **Ajouter un nouvel élément** s’affiche.  
  
4.  Sélectionnez **classe COM** à partir de la **modèles** liste, puis cliquez sur **ajouter**. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Ajoute une nouvelle classe et configure le nouveau projet pour COM interop.  
  
5.  Ajoutez le code tels que les propriétés, méthodes et événements à la classe COM.  
  
6.  Sélectionnez **générer ClassLibrary1** à partir de la **générer** menu. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]génère l’assembly et inscrit l’objet COM avec le système d’exploitation.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Création d’objets COM sans le modèle de classe COM  
 Vous pouvez également créer une classe COM manuellement au lieu de l’aide du modèle de classe COM. Cette procédure est utile lorsque vous travaillez à partir de la ligne de commande ou lorsque vous souhaitez mieux contrôler la façon dont les objets COM sont définies.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Pour configurer votre projet pour générer un objet COM  
  
1.  Ouvrez un nouveau projet d’Application Windows à partir de la **fichier** en cliquant sur **NewProject**.  
  
2.  Dans le **nouveau projet** boîte de dialogue sous le **Types de projets** champ, vérifiez que Windows est sélectionné. Sélectionnez **bibliothèque de classes** à partir de la **modèles** liste, puis cliquez sur **OK**. Le nouveau projet s’affiche.  
  
3.  Dans **l’Explorateur de solutions**, avec le bouton droit de votre projet, puis cliquez sur **propriétés**. Le **Concepteur de projets** s’affiche.  
  
4.  Cliquez sur l’onglet **Compiler**.  
  
5.  Sélectionnez le **inscrire pour COM Interop** case à cocher.  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Pour définir le code dans votre classe pour créer un objet COM.  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur **Class1.vb** pour afficher son code.  
  
2.  Renommez la classe `ComClass1`.  
  
3.  Ajoutez les constantes suivantes à `ComClass1`. Ils stockera les constantes GUID (Globally Unique Identifier) qui les objets COM doivent obligatoirement avoir.  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  Dans le menu **Outils**, cliquez sur **Créer un Guid**. Dans la boîte de dialogue **Créer un Guid**, cliquez sur **Format du Registre**, puis sur **Copier**. Cliquez sur **Quitter**.  
  
5.  Remplacez la chaîne vide pour la `ClassId` avec le GUID, les accolades suppression le début et de fin. Par exemple, si le GUID fourni par Guidgen est `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , votre code doit apparaître comme suit.  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  Répétez les étapes précédentes pour le `InterfaceId` et `EventsId` constantes, comme dans l’exemple suivant.  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  Assurez-vous que les GUID sont nouveaux et uniques ; dans le cas contraire, votre composant COM pourrait être en conflit avec d’autres composants.  
  
7.  Ajouter le `ComClass` attribut `ComClass1`, en spécifiant les GUID pour l’ID de classe, les ID d’Interface et les ID des événements comme dans l’exemple suivant :  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  Classes COM doivent avoir un sans paramètre `Public Sub New()` constructeur ou la classe n’est pas inscrite correctement. Ajoutez un constructeur sans paramètre à la classe :  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. Ajouter des propriétés, méthodes et événements à la classe, en terminant par un `End Class` instruction. Sélectionnez **générer la Solution** à partir de la **générer** menu. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]génère l’assembly et inscrit l’objet COM avec le système d’exploitation.  
  
    > [!NOTE]
    >  Les objets COM que vous générez avec [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ne peut pas être utilisé par d’autres [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] applications, car ils ne sont pas des objets COM trues. Tente d’ajouter des références à ces objets COM génère une erreur. Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Procédure pas à pas : implémentation de l’héritage avec les objets COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [#Region (directive)](../../../visual-basic/language-reference/directives/region-directive.md)  
 [Interopérabilité COM dans les applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Dépannage des problèmes liés à l’interopérabilité](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
