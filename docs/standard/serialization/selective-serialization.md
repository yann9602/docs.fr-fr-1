---
title: "Sérialisation sélective"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f583c0c7f2895b16ac0aea883dd98b4768179127
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="selective-serialization"></a><span data-ttu-id="1e853-102">Sérialisation sélective</span><span class="sxs-lookup"><span data-stu-id="1e853-102">Selective serialization</span></span>
<span data-ttu-id="1e853-103">Une classe contient souvent des champs qui ne doivent pas être sérialisés.</span><span class="sxs-lookup"><span data-stu-id="1e853-103">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="1e853-104">Par exemple, supposez qu'une classe stocke un ID de thread dans une variable membre.</span><span class="sxs-lookup"><span data-stu-id="1e853-104">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="1e853-105">Quand la classe est désérialisée, il se peut que le thread stocké pour l’ID au moment de la sérialisation de la classe ne s’exécute plus. La sérialisation de cette valeur est donc inutile.</span><span class="sxs-lookup"><span data-stu-id="1e853-105">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="1e853-106">Vous pouvez empêcher des variables membres d’être sérialisées en les marquant avec l’attribut [NonSerialized](xref:System.NonSerializedAttribute) comme suit.</span><span class="sxs-lookup"><span data-stu-id="1e853-106">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="1e853-107">Si possible, faites en sorte qu'un objet pouvant contenir des données de sécurité sensibles soit non sérialisable.</span><span class="sxs-lookup"><span data-stu-id="1e853-107">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="1e853-108">Si l’objet doit être sérialisé, appliquez l’attribut `NonSerialized` aux champs spécifiques qui stockent des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="1e853-108">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="1e853-109">Si vous n’excluez pas ces champs de la sérialisation, notez que les données qu’ils stockent sont exposées à tout code autorisé à sérialiser.</span><span class="sxs-lookup"><span data-stu-id="1e853-109">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="1e853-110">Pour plus d’informations sur l’écriture de code de sérialisation sécurisé, consultez [Sécurité et sérialisation](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="1e853-110">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="1e853-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e853-111">See also</span></span>  
 [<span data-ttu-id="1e853-112">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="1e853-112">Binary Serialization</span></span>](binary-serialization.md)  
 [<span data-ttu-id="1e853-113">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="1e853-113">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)  
 [<span data-ttu-id="1e853-114">Sécurité et sérialisation</span><span class="sxs-lookup"><span data-stu-id="1e853-114">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)