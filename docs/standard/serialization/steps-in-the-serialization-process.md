---
title: "Étapes du processus de sérialisation"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: a4c125493e1b59d329bf4626c45f48b2b222d308
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="steps-in-the-serialization-process"></a>Étapes du processus de sérialisation
Quand la méthode <xref:System.Runtime.Serialization.Formatter.Serialize*> est appelée sur un [formateur](xref:System.Runtime.Serialization.Formatter), la sérialisation de l’objet s’effectue d’après la séquence de règles suivante :

- Un contrôle est effectué pour déterminer si le formateur possède un sélecteur de substitut. Si tel est le cas, vérifiez si le sélecteur de substitut gère des objets du type donné. Si le sélecteur gère le type d’objet, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=fullName> est appelée sur le sélecteur de substitution.

- S’il n’existe aucun sélecteur de substitution ou s’il ne gère pas ce type d’objet, un contrôle est effectué pour déterminer si l’objet est marqué avec l’attribut [Serializable](xref:System.SerializableAttribute). S’il ne l’est pas, une exception <xref:System.Runtime.Serialization.SerializationException> est levée.

- Si l’objet est marqué convenablement, vérifiez s’il implémente l’interface <xref:System.Runtime.Serialization.ISerializable>. Si tel est le cas, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> est appelée sur l’objet.
  
- Si l’objet n’implémente pas <xref:System.Runtime.Serialization.ISerializable>, la stratégie de sérialisation par défaut est utilisée. Elle permet de sérialiser tous les champs non marqués comme [NonSerialized](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation binaire](binary-serialization.md)   
 [Sérialisation XML et SOAP](xml-and-soap-serialization.md)
