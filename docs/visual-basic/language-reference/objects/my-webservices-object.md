---
title: "My.WebServices Object | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.WebServices"
  - "My.MyProject.WebServices"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.WebServices object"
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# My.WebServices Object
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Fournit des propriétés permettant de créer et d'accéder à une instance unique de chaque service Web XML référencé par le projet en cours.  
  
## Notes  
 L'objet `My.WebServices` fournit une instance de chaque service Web référencé par le projet actuel.  Chaque instance est instanciée sur demande.  Vous pouvez accéder à ces services Web via les propriétés de l'objet `My.WebServices`.  La propriété porte le même nom que celui du service Web auquel la propriété accède.  Toute classe qui hérite de <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> est un service Web.  Pour plus d'informations sur l'ajout de services Web à un projet, consultez [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 L'objet `My.WebServices` n'expose que les services Web associés au projet actuel.  Il ne fournit pas un accès aux services Web déclarés dans les DLL référencées.  Pour accéder à un service Web fourni par une DLL, vous devez utiliser le nom qualifié du service Web, sous la forme *DllName*.*WebServiceName*.  Pour plus d'informations, consultez [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 L'objet et ses propriétés ne sont pas disponibles pour les applications Web.  
  
## Propriétés  
 Chaque propriété de l'objet `My.WebServices` fournit l'accès à une instance d'un service Web référencé par le projet actuel.  La propriété porte le même que celui du service Web auquel accède la propriété et le type de propriété porte le même nom que le type de service Web.  
  
> [!NOTE]
>  Si une collision de noms se produit, le nom de la propriété pour accéder à un service Web est *RootNamespace*\_*Namespace*\_*FormName*.  Par exemple, considérez deux services Web nommés `Service1`.  Si l'un de ces services se trouve dans l'espace de noms racine `WindowsApplication1` et dans l'espace de noms `Namespace1`, vous accédez à ce service en utilisant `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Lorsque vous accédez en premier lieu à l'une des propriétés de l'objet `My.WebServices`, il crée une instance du service Web et le stocke.  Les accès ultérieurs de cette propriété retournent cette instance du service Web.  
  
 Vous pouvez supprimer un service Web en assignant `Nothing` à la propriété de ce service Web.  L'accesseur Set de la propriété assigne `Nothing` à la valeur stockée.  Si vous assignez une valeur autre que `Nothing` à la propriété, l'accesseur Set lève une exception <xref:System.ArgumentException>.  
  
 Vous pouvez tester si une propriété de l'objet `My.WebServices` stocke une instance du service Web à l'aide de l'opérateur `Is` ou `IsNot`.  Vous pouvez utiliser ces opérateurs pour vérifier si la propriété a la valeur `Nothing`.  
  
> [!NOTE]
>  En général, l'opérateur `Is` ou `IsNot` doit lire la valeur de la propriété pour effectuer la comparaison.  Toutefois, si la propriété stocke actuellement `Nothing`, la propriété crée une instance du service Web, puis la retourne.  Néanmoins, le compilateur Visual Basic traite spécialement les propriétés de l'objet `My.WebServices` et permet à l'opérateur `Is` ou `IsNot` de vérifier l'état de la propriété sans modifier sa valeur.  
  
## Exemple  
 Cet exemple appelle la méthode `FahrenheitToCelsius` du service Web XML `TemperatureConverter` et retourne le résultat.  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/visualbasic/VbVbalrMyWebService/Form1.vb#1)]  
  
 Pour que cet exemple fonctionne, votre projet doit référencer un service Web appelé `Converter` et ce dernier exposer la méthode `ConvertTemperature`.  Pour plus d'informations, consultez [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Ce code ne fonctionne pas dans un projet d'application Web.  
  
## Configuration requise  
  
### Disponibilité par type de projet  
  
|||  
|-|-|  
|Type de projet|Disponible|  
|Application Windows|**Oui**|  
|Bibliothèque de classes|**Oui**|  
|Application console|**Oui**|  
|Bibliothèque de contrôles Windows|**Oui**|  
|Bibliothèque de contrôles Web|**Oui**|  
|Service Windows|**Oui**|  
|Site Web|Non|  
  
## Voir aussi  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>   
 <xref:System.ArgumentException>   
 [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)