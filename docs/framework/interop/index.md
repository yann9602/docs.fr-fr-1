---
title: "Interopération avec du code non managé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ff86b062efddde6f97555efb97247f60a6e1db98
ms.contentlocale: fr-fr
ms.lasthandoff: 09/18/2017

---
# <a name="interoperating-with-unmanaged-code"></a>Interopération avec du code non managé
Le .NET Framework assure l’interaction avec les composants COM, les services COM+, les bibliothèques de types externes et de nombreux services de systèmes d’exploitation. Les types de données, les signatures de méthode et les mécanismes de gestion des erreurs varient selon les modèles objet managés et non managés. Pour simplifier l’interopérabilité entre les composants .NET Framework et le code non managé ainsi que pour faciliter la migration, le common language runtime dissimule à la fois aux clients et aux serveurs les différences entre ces modèles objet.  
  
 Le code qui s’exécute sous le contrôle du runtime est appelé code managé. Inversement, le code qui s’exécute en dehors du runtime est appelé code non managé. Les composants COM, les interfaces ActiveX et les fonctions API Win32 sont des exemples de code non managé.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Rubriques Comment sur l’interopérabilité avec du code non managé](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 Fournit des liens vers toutes les rubriques de guide pratique qui se trouvent dans la documentation conceptuelle relative à l’interopérabilité avec du code non managé.  
  
 [Exposition de composants COM au .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 Explique comment utiliser des composants COM à partir d’applications .NET Framework.  
  
 [Exposition de composants .NET Framework à COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 Explique comment utiliser des composants .NET Framework à partir d’applications COM.  
  
 [Consommation de fonctions DLL non managées](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Décrit comment appeler des fonctions DLL non managées à l’aide de l’appel de code non managé.  
  
 [Considérations de design pour l’interopérabilité](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 Fournit des conseils pour l'écriture de composants COM intégrés.  
  
 [Marshaling d’interopérabilité](../../../docs/framework/interop/interop-marshaling.md)  
 Décrit le marshaling de COM Interop et de l’appel de code non managé.  
  
 [Guide pratique pour mapper des HRESULT et des exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 Décrit le mappage entre les exceptions et les valeurs HRESULT.  
  
 [Interopérabilité à l’aide de types génériques](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 Décrit le comportement de types génériques en cas d’utilisation dans COM Interop.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Interopérabilité COM avancée](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 Fournit des liens vers des informations sur l'incorporation de composants COM dans une application .NET Framework.

