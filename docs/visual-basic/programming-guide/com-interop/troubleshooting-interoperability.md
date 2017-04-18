---
title: "Résolution des problèmes d’interopérabilité (Visual Basic) | Documents Microsoft"
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
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability
- interoperability, troubleshooting
- COM interop, troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: cbc37638ed5c57b94356c2d189f36b66202ceba5
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-interoperability-visual-basic"></a>Dépannage des problèmes liés à l'interopérabilité (Visual Basic)
Lors d’interopérations entre COM et le code managé de la [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], vous pouvez rencontrer un ou plusieurs des problèmes courants suivants.  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a>Marshaling d’interopérabilité  
 Dans certains cas, vous devrez utiliser des types de données qui ne sont pas inclus dans le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Assemblys d’interopérabilité gèrent la plupart du travail pour les objets COM, mais vous devrez peut-être contrôler les types de données qui sont utilisés lorsque des objets managés sont exposés à COM. Par exemple, les structures de bibliothèques de classes doivent indiquer le `BStr` non managé de type sur les chaînes envoyées à des objets COM créés par Visual Basic 6.0 et versions antérieures. Dans ce cas, vous pouvez utiliser la <xref:System.Runtime.InteropServices.MarshalAsAttribute>attribut pour que les types managés à exposer en tant que types non managés.</xref:System.Runtime.InteropServices.MarshalAsAttribute>  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a>Exportation de chaînes de longueur fixe au Code non managé  
 Dans Visual Basic 6.0 et versions antérieures, les chaînes sont exportées dans les objets COM comme des séquences d’octets sans caractère null de fin. Pour assurer la compatibilité avec d’autres langages, [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] inclut un caractère de fin lors de l’exportation de chaînes. La meilleure façon de résoudre cette incompatibilité consiste à exporter les chaînes qui n’ont pas ce caractère comme des tableaux de `Byte` ou `Char`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a>Exportation de hiérarchies d’héritage  
 Hiérarchies aplatissent les lorsqu’elle est exposée en tant qu’objets COM de classe managée. Par exemple, si vous définissez une classe de base avec un membre, puis héritez de la classe de base dans une classe dérivée qui est exposée comme un objet COM, les clients qui utilisent la classe dérivée de l’objet COM ne sera pas en mesure d’utiliser les membres hérités. Membres de classe de base sont accessibles à partir des objets COM que comme des instances d’une classe de base et uniquement si la classe de base est également créée comme un objet COM.  
  
## <a name="overloaded-methods"></a>Méthodes surchargées  
 Bien que vous puissiez créer des méthodes surchargées avec [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], elles ne sont pas prises en charge par COM. Lorsqu’une classe qui contient des méthodes surchargées est exposée comme un objet COM, les nouveaux noms de méthodes sont générés pour les méthodes surchargées.  
  
 Par exemple, considérez une classe qui a deux surcharges de la `Synch` méthode. Lorsque la classe est exposée comme un objet COM, les nouveaux noms de méthode générée peut être `Synch` et `Synch_2`.  
  
 Le changement de nom peut provoquer deux problèmes pour les consommateurs de l’objet COM.  
  
1.  Les noms de méthodes générés ne soient pas accessibles par les clients.  
  
2.  Les noms de méthode générée dans la classe exposée comme objet COM peuvent changer lorsque de nouvelles surcharges sont ajoutées à la classe ou sa classe de base. Cela peut entraîner des problèmes de versioning.  
  
 Pour résoudre ces deux problèmes, donnez à chaque méthode un nom unique, au lieu d’utiliser la surcharge, lorsque vous développez des objets qui seront exposées en tant qu’objets COM.  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a>Utilisation d’objets COM via les assemblys d’interopérabilité  
 Vous utilisez des assemblys PIA presque comme s’ils étaient des remplacements de code managé pour les objets COM qu’ils représentent. Toutefois, car ils sont des wrappers et des objets COM réels pas, il existe certaines différences entre l’utilisation d’assemblys d’interopérabilité et d’assemblys standard. Ces différences comprennent l’exposition des classes et des types de données pour les paramètres et valeurs de retour.  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a>Classes exposées en tant que les deux Interfaces et Classes  
 Contrairement aux classes dans les assemblys standard, les classes COM sont exposées dans les assemblys comme une interface et une classe qui représente la classe COM interop. Nom de l’interface est identique à celui de la classe COM. Le nom de la classe d’interopérabilité est le même que celui de la classe COM d’origine, mais avec le mot « Classe » est ajouté. Par exemple, supposons que vous avez un projet avec une référence à un assembly d’interopérabilité pour un objet COM. Si la classe COM est nommée `MyComClass`, IntelliSense et l’Explorateur d’objets affichent une interface nommée `MyComClass` et une classe nommée `MyComClassClass`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a>Création d’Instances d’une classe .NET Framework  
 En général, vous créez une instance d’un [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] à l’aide de la classe la `New` instruction avec un nom de classe. Une classe COM représentée par un assembly d’interopérabilité est le seul cas dans lequel vous pouvez utiliser la `New` instruction avec une interface. Sauf si vous utilisez la classe COM avec une `Inherits` instruction, vous pouvez utiliser l’interface comme vous le feriez pour une classe. Le code suivant montre comment créer un `Command` objet dans un projet qui fait référence à l’objet COM de la bibliothèque Microsoft ActiveX Data Objects 2.8 :  
  
 [!code-vb[VbVbalrInterop&#20;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 Toutefois, si vous utilisez la classe COM comme base pour une classe dérivée, vous devez utiliser la classe d’interopérabilité qui représente la classe COM, comme dans le code suivant :  
  
 [!code-vb[VbVbalrInterop n °&21;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  Assemblys d’interopérabilité implémentent de façon implicite les interfaces qui représentent des classes COM.. Vous ne devez pas essayer d’utiliser le `Implements` entraîne d’instruction pour implémenter ces interfaces ou une erreur.  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a>Types de données pour les paramètres et valeurs de retour  
 Contrairement aux membres des assemblys standards, assembly d’interopérabilité peuvent posséder des types de données qui diffèrent de ceux utilisés dans la déclaration d’objet d’origine. Même si les assemblys d’interopérabilité convertissent implicitement les types COM compatible types common language runtime, vous devez prêter attention aux types de données qui sont utilisées par les deux côtés pour éviter les erreurs d’exécution. Par exemple, dans les objets COM créés dans Visual Basic 6.0 et les versions antérieures, les valeurs de type `Integer` supposent la [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] type équivalent, `Short`. Il est recommandé d’utiliser l’Explorateur d’objets pour examiner les caractéristiques des membres importés avant de les utiliser.  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a>Méthodes COM de niveau module  
 La plupart des objets COM sont utilisés en créant une instance d’une classe COM à l’aide du `New` (mot clé), puis en appelant les méthodes de l’objet. Une exception à cette règle implique des objets COM qui contiennent des `AppObj` ou `GlobalMultiUse` des classes COM. Ces classes ressemblent à des méthodes de niveau module dans [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] classes. Visual Basic 6.0 et les versions antérieures créent implicitement des instances de ces objets pour vous la première fois que vous appelez l’une de leurs méthodes. Par exemple, dans Visual Basic 6.0, vous pouvez ajouter une référence à la bibliothèque d’objets Microsoft DAO 3.6 et appeler la `DBEngine` méthode sans d’abord créer une instance :  
  
```  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]nécessite toujours créer les instances des objets COM avant de pouvoir utiliser leurs méthodes. Pour utiliser ces méthodes dans [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)], déclarez une variable de la classe souhaitée et utilisez le mot clé new pour attribuer l’objet à la variable objet. Le `Shared` mot clé peut être utilisé lorsque vous souhaitez vous assurer que qu’une seule instance de la classe est créée.  
  
 [!code-vb[VbVbalrInterop n °&23;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a>Erreurs non gérées dans les gestionnaires d’événements  
 Un problème d’interopérabilité courant concerne les erreurs dans les gestionnaires d’événements qui gèrent les événements déclenchés par des objets COM. Ces erreurs sont ignorées, sauf si vous les recherchez spécifiquement à l’aide `On Error` ou `Try...Catch...Finally` instructions. Par exemple, l’exemple suivant provient un [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] projet qui fait référence à l’objet COM de la bibliothèque Microsoft ActiveX Data Objects 2.8.  
  
 [!code-vb[VbVbalrInterop&#24;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 Cet exemple génère une erreur comme prévu. Toutefois, si vous essayez le même exemple sans le `Try...Catch...Finally` bloc, l’erreur est ignorée comme si vous avez utilisé la `OnError Resume Next` instruction. Sans la gestion des erreurs, la division par zéro échoue silencieusement. Étant donné que ces erreurs ne déclenchent jamais les erreurs d’exception non gérée, il est important que vous utilisez une forme de gestion des exceptions dans les gestionnaires d’événements qui gèrent les événements provenant des objets COM.  
  
### <a name="understanding-com-interop-errors"></a>Compréhension des erreurs COM interop  
 Sans la gestion des erreurs, les appels interop génèrent souvent des erreurs qui fournissent peu d’informations. Si possible, utilisez structurées gestion des erreurs pour fournir plus d’informations sur les problèmes lorsqu’ils se produisent. Cela peut être particulièrement utile lorsque vous déboguez des applications. Exemple :  
  
 [!code-vb[VbVbalrInterop&#25;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 Vous trouverez des informations telles que la description de l’erreur HRESULT et la source des erreurs COM en examinant le contenu de l’objet exception.  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a>Problèmes de contrôle ActiveX  
 La plupart des contrôles ActiveX qui fonctionnent avec Visual Basic 6.0 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] sans problème. Les principales exceptions sont les contrôles conteneurs, ou des contrôles qui contiennent visuellement d’autres contrôles. Quelques exemples d’anciens contrôles qui ne fonctionnent pas correctement avec [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] sont les suivantes :  
  
-   Contrôle Frame de Microsoft Forms 2.0  
  
-   Contrôle Up-Down, également connu sous le contrôle spin  
  
-   Contrôle Sheridan Tab  
  
 Il existe peu de solutions pour les problèmes de contrôle ActiveX non pris en charge. Vous pouvez migrer les contrôles existants à [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] si vous possédez le code source d’origine. Sinon, vous pouvez vérifier avec les éditeurs de logiciels pour la mise à jour. Versions compatibles NET de remplacer les contrôles non pris en charge les contrôles ActiveX.  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a>Transmission des propriétés ReadOnly de contrôles avec ByRef  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]génère parfois des erreurs COM telles que « Error 0x800A017F CTL_E_SETNOTSUPPORTED » lorsque vous transmettez `ReadOnly` propriétés de certains anciens contrôles ActiveX comme `ByRef` paramètres à d’autres procédures. Appels de procédure similaires à partir de Visual Basic 6.0 ne génèrent pas d’erreur et les paramètres sont traités comme si vous les transmettiez par valeur. Le message d’erreur s’affiche dans [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] est l’objet COM reporting que vous essayez de modifier une propriété qui ne possède pas de propriété `Set` procédure.  
  
 Si vous avez accès à la procédure appelée, vous pouvez éviter cette erreur en utilisant le `ByVal` (mot clé) pour déclarer des paramètres qui acceptent `ReadOnly` propriétés. Exemple :  
  
 [!code-vb[VbVbalrInterop&#26;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 Si vous n’avez pas accès au code source pour la procédure appelée, vous pouvez forcer la propriété être passés par valeur en ajoutant un jeu supplémentaire de crochets autour de la procédure d’appel. Par exemple, dans un projet qui fait référence à l’objet COM de la bibliothèque Microsoft ActiveX Data Objects 2.8, vous pouvez utiliser :  
  
 [!code-vb[27 VbVbalrInterop](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a>Déploiement d’assemblys exposant l’interopérabilité  
 Déploiement d’assemblys qui exposent les interfaces COM soulève des défis uniques. Par exemple, un problème se produit lorsque des applications distinctes référencent le même assembly COM.. Cette situation est courante lorsqu’une nouvelle version d’un assembly est installée et une autre application utilise toujours l’ancienne version de l’assembly. Si vous désinstallez un assembly partageant une DLL, vous pouvez involontairement rendre indisponible aux autres assemblys.  
  
 Pour éviter ce problème, vous devez installer les assemblys partagés vers le Global Assembly Cache (GAC) et utiliser un module de fusion pour le composant. Si vous ne pouvez pas installer l’application dans le GAC, il doit être installé dans un sous-répertoire spécifique à la version du répertoire CommonFilesFolder.  
  
 Assemblys qui ne sont pas partagés doivent être placés côte à côte dans le répertoire avec l’application appelante.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)   
 [Tlbexp.exe (exportateur de bibliothèques)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)   
 [Procédure pas à pas : Implémentation de l’héritage avec les objets COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Inherits (instruction)](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)
