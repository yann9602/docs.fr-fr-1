---
title: "Wrapper pouvant être appelé par le runtime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, COM wrappers
- RCW
- COM wrappers
- runtime callable wrappers
- interoperation with unmanaged code, COM wrappers
ms.assetid: 7e542583-1e31-4e10-b523-8cf2f29cb4a4
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 722a317a01d79f56496810b8727ce041705c8f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-callable-wrapper"></a>Wrapper pouvant être appelé par le runtime
Le common language runtime expose les objets COM via un proxy appelé wrapper RCW. Même si le wrapper RCW est un objet ordinaire pour les clients .NET, sa fonction principale est de marshaler les appels entre un client .NET et un objet COM.  
  
 Le runtime crée un wrapper RCW pour chaque objet COM, quel que soit le nombre de références qui existent sur cet objet. Le runtime gère un seul wrapper RCW par processus pour chaque objet.  Si vous créez un wrapper RCW dans un domaine d'application ou cloisonnement, puis passez une référence à un autre domaine d'application ou cloisonnement, un proxy du premier objet sera utilisé.  Comme le montre l'illustration suivante, il n'existe pas de limite au nombre de clients managés pouvant contenir une référence aux objets COM qui exposent les interfaces INew et INewer.  
  
 ![Wrapper RCW](../../../docs/framework/interop/media/rcw.gif "rcw")  
Accès aux objets COM via le wrapper RCW  
  
 À l'aide de métadonnées dérivées d'une bibliothèque de types, le runtime crée l'objet COM appelé, ainsi qu'un wrapper pour celui-ci. Chaque wrapper RCW gère un cache de pointeurs d'interface sur l'objet COM qu'il encapsule et libère sa référence à l'objet COM quand le wrapper RCW n'est plus utile. Le runtime exécute le garbage collection du wrapper RCW.  
  
 Entre autres activités, le wrapper RCW marshale les données entre code managé et non managé, pour le compte de l'objet encapsulé. Plus précisément, le wrapper RCW fournit le marshaling pour les arguments de méthode et les valeurs de retour de méthode chaque fois que le client et le serveur ont des représentations différentes des données circulant entre eux.  
  
 Le wrapper standard applique les règles de marshaling intégrées. Par exemple, quand un client .NET passe un type String dans le cadre d'un argument à un objet non managé, le wrapper convertit la chaîne en un type BSTR. Si l'objet COM retourne un BSTR à son appelant managé, l'appelant reçoit une chaîne (String). Le client et le serveur envoient et reçoivent des données qui leur sont familières. Les autres types ne nécessitent pas de conversion. Par exemple, un wrapper standard passera toujours un entier de 4 octets d'un code managé à un code non managé sans convertir le type.  
  
## <a name="marshaling-selected-interfaces"></a>Marshaling d’interfaces sélectionnées  
 L’objectif principal du [wrapper RCW](../../../docs/framework/interop/runtime-callable-wrapper.md) est de masquer les différences entre les modèles de programmation managé et non managé. Pour créer une transition transparente, le wrapper RCW consomme les interfaces COM sélectionnées sans les exposer au client .NET, comme indiqué dans l'illustration suivante.  
  
 ![Wrapper RCW avec interfaces](../../../docs/framework/interop/media/rcwwithinterfaces.gif "rcwwithinterfaces")  
Les interfaces COM et le wrapper RCW  
  
 Quand il est créé comme un objet à liaison anticipée, le wrapper RCW est un type spécifique. Il implémente les interfaces que l'objet COM implémente et expose les méthodes, les propriétés et les événements des interfaces de l'objet. Dans l’illustration, le wrapper RCW expose l’interface INew, mais consomme les interfaces **IUnknown** et **IDispatch**. De plus, le wrapper RCW expose tous les membres de l'interface INew au client .NET.  
  
 Le wrapper RCW consomme les interfaces répertoriées dans le tableau suivant, qui sont exposées par l'objet qu'il encapsule.  
  
|Interface|Description|  
|---------------|-----------------|  
|**IDispatch**|Pour la liaison tardive aux objets COM via la réflexion.|  
|**IErrorInfo**|Fournit une description textuelle de l’erreur, sa source, un fichier d’aide, un contexte d’aide et le GUID de l’interface ayant défini l’erreur (toujours **GUID_NULL** pour les classes .NET).|  
|**IProvideClassInfo**|Si l’objet COM qui est encapsulé implémente **IProvideClassInfo**, le wrapper RCW extrait les informations de type à partir de cette interface pour fournir une meilleure identité de type.|  
|**IUnknown**|Pour l'identité de l'objet, le forçage de type et la gestion de la durée de vie :<br /><br /> - Identité d’un objet<br />     Le runtime fait la distinction entre les objets COM en comparant la valeur d’interface **IUnknown** pour chaque objet.<br />- Forçage de type<br />     Le wrapper RCW reconnaît la découverte de type dynamique exécutée par la méthode **QueryInterface**.<br />- Gestion de la durée de vie<br />     À l’aide de la méthode **QueryInterface**, le wrapper RCW obtient et conserve une référence à un objet non managé jusqu’à ce que le runtime exécute le garbage collection sur le wrapper, qui libère l’objet non managé.|  
  
 Le wrapper RCW peut éventuellement consommer les interfaces répertoriées dans le tableau suivant, qui sont exposées par l'objet qu'il encapsule.  
  
|Interface|Description|  
|---------------|-----------------|  
|**IConnectionPoint** et **IConnectionPointContainer**|Le wrapper RCW convertit les objets qui exposent le style d'événement point de connexion en événements basés sur le délégué.|  
|**IDispatchEx**|Si la classe implémente **IDispatchEx**, le wrapper RCW implémente **IExpando**. L’interface **IDispatchEx** est une extension de l’interface **IDispatch** qui, contrairement à l’interface **IDispatch**, permet l’énumération, l’ajout, la suppression et l’appel sensible à la casse des membres.|  
|**IEnumVARIANT**|Permet aux types COM qui prennent en charge les énumérations d’être traités comme des collections.|  
  
## <a name="see-also"></a>Voir aussi  
 [Wrappers COM](../../../docs/framework/interop/com-wrappers.md)  
 [Marshaling d’Interfaces sélectionnées](http://msdn.microsoft.com/en-us/fdb97fd0-f694-4832-bf15-a4e7cf413840)  
 [Wrapper CCW (COM Callable Wrapper)](../../../docs/framework/interop/com-callable-wrapper.md)  
 [Récapitulatif de la conversion d’une bibliothèque de types en assembly](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 [Importation d'une bibliothèque de types sous la forme d'un assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
