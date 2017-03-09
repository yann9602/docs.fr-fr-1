---
title: "Troubleshooting Interoperability (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interop, deploying assemblies"
  - "assemblies [Visual Basic]"
  - "interop, installing assemblies that share components"
  - "COM objects, troubleshooting"
  - "interop, sharing components"
  - "troubleshooting interoperability"
  - "interoperability, troubleshooting"
  - "COM interop, troubleshooting"
  - "assemblies [Visual Basic], deploying"
  - "troubleshooting Visual Basic, interoperability"
  - "interop assemblies"
  - "interoperability, sharing components"
  - "shared components, using with assemblies"
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Troubleshooting Interoperability (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Lors d'interopérations entre COM et le code managé du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)], un ou plusieurs des problèmes courants suivants peuvent se poser.  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a> Marshaling d'interopérabilité  
 Il se peut que vous devez parfois utiliser des types de données qui ne font pas partie du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)].  Les assemblys d'interopérabilité gèrent la plupart du travail pour les objets COM, mais vous devez peut\-être contrôler les types de données utilisés lorsque des objets managés sont exposés à COM.  Par exemple, les structures des bibliothèques de classes doivent indiquer le type non managé `BStr` sur les chaînes envoyées à des objets COM créés par Visual Basic 6.0 et par des versions antérieures.  Dans ce cas, vous pouvez utiliser l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> pour que les types managés soient exposés en tant que types non managés.  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a> Exportation de chaînes de longueur fixe dans du code non managé  
 Dans Visual Basic 6.0 et les versions antérieures, les chaînes sont exportées dans les objets COM sous la forme de séquences d'octets sans caractère null de fin.  Dans un souci de compatibilité avec d'autres langages, [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] inclut un caractère de fin lors de l'exportation de chaînes.  La meilleure façon de résoudre cette incompatibilité consiste à exporter les chaînes qui n'ont pas ce caractère comme des tableaux de `Byte` ou `Char`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a> Exportation de hiérarchies d'héritage  
 Les hiérarchies de classes managées s'aplatissent lorsqu'elles sont exposées sous forme d'objets COM.  Par exemple, si vous définissez une classe de base avec un membre, puis héritez de cette classe dans une classe dérivée qui est exposée sous forme d'objet COM, les clients qui utilisent la classe dérivée dans l'objet COM ne sont pas en mesure d'utiliser les membres hérités.  Les membres de la classe de base ne sont accessibles à partir d'objets COM que sous forme d'instances d'une classe de base, et uniquement si la classe de base est également créée sous forme d'objet COM.  
  
## Méthodes surchargées  
 Bien que vous puissiez créer des méthodes surchargées avec [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], elles ne sont pas prises en charge par COM.  Lorsqu'une classe qui contient des méthodes surchargées est exposée comme objet COM, de nouveaux noms de méthodes sont générés pour les méthodes surchargées.  
  
 Par exemple, considérez une classe avec deux surcharges de la méthode `Synch`.  Lorsque la classe est exposée comme objet COM, les nouveaux noms de méthodes générés peuvent être `Synch` et `Synch_2`.  
  
 Le changement de nom peut provoquer deux problèmes pour les consommateurs de l'objet COM.  
  
1.  Il se peut que les clients n'attendent pas les noms de méthodes générés.  
  
2.  Les noms de méthodes générés dans la classe exposée comme objet COM peuvent changer lorsque de nouvelles surcharges sont ajoutées à la classe ou sa classe de base.  Ce qui peut provoquer des problèmes de versioning.  
  
 Pour résoudre les deux problèmes, donnez à chaque méthode un nom unique au lieu d'utiliser la surcharge, lors du développement d'objets qui seront exposés comme objets COM.  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a> Utilisation d'objets COM via les assemblys d'interopérabilité  
 Vous utilisez presque les assemblys d'interopérabilité comme s'il s'agissait de remplacements de code managé pour les objets COM qu'ils représentent.  Toutefois, dans la mesure où ce sont des wrappers et non des objets COM réels, il existe quelques différences entre l'utilisation d'assemblys d'interopérabilité et celle d'assemblys standard.  Ces différences comprennent l'exposition des classes ainsi que les types de données pour les paramètres et les valeurs de retour.  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a> Classes exposées à la fois sous forme d'interfaces et de classes  
 À la différence des classes dans les assemblys standard, les classes COM sont exposées dans les assemblys d'interopérabilité à la fois sous la forme d'une interface et d'une classe qui représente la classe COM.  Le nom de l'interface est identique à celui de la classe COM.  Le nom de la classe d'interopérabilité est le même que celui de la classe COM d'origine, auquel le mot "Class" a été ajouté.  Par exemple, supposons que vous avez un projet avec une référence à un assembly d'interopérabilité pour un objet COM.  Si le nom de la classe COM est `MyComClass`, IntelliSense et l'Explorateur d'objets affichent une interface nommée `MyComClass` et une classe nommée `MyComClassClass`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a> Création d'instances d'une classe .NET Framework  
 En règle générale, vous créez une instance d'une classe [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] en utilisant l'instruction `New` avec un nom de classe.  Le fait d'avoir une classe COM représentée par un assembly d'interopérabilité est le seul cas dans lequel vous pouvez utiliser l'instruction `New` avec une interface.  À moins d'utiliser la classe COM avec une instruction `Inherits`, vous pouvez utiliser l'interface de la même manière qu'une classe.  Le code suivant montre comment créer un objet `Command` dans un projet qui fait référence à l'objet COM de la bibliothèque Microsoft ActiveX Data Objects 2.8 :  
  
 [!code-vb[VbVbalrInterop#20](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#20)]  
  
 Toutefois, si vous utilisez la classe COM comme base d'une classe dérivée, vous devez utiliser la classe d'interopérabilité qui représente la classe COM, comme dans le code suivant :  
  
 [!code-vb[VbVbalrInterop#21](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#21)]  
  
> [!NOTE]
>  Les assemblys d'interopérabilité implémentent de façon implicite les interfaces qui représentent des classes COM.  Vous ne devez pas essayer d'utiliser l'instruction `Implements` pour implémenter ces interfaces afin de ne pas provoquer d'erreur.  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a> Types de données pour les paramètres et valeurs de retour  
 À la différence des membres des assemblys standard, ceux des assemblys d'interopérabilité peuvent posséder des types de données différents de ceux utilisés dans la déclaration initiale de l'objet.  Même si les assemblys d'interopérabilité convertissent de façon implicite les types COM en types Common Language Runtime compatibles, vous devez prêter attention aux types de données utilisés des deux côtés pour éviter les erreurs d'exécution.  Par exemple, dans les objets COM créés avec Visual Basic 6.0 et les versions antérieures, les valeurs du type `Integer` adoptent le type [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] équivalent, `Short`.  Il est recommandé d'utiliser l'Explorateur d'objets pour examiner les caractéristiques des membres importés avant de les utiliser.  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a> Méthodes COM de niveau module  
 La plupart des objets COM sont utilisés par la création d'une instance de classe COM avec le mot clé `New`, puis par l'appel aux méthodes associées à ces objets.  Une exception à cette règle concerne les objets COM qui contiennent des classes COM `AppObj` ou `GlobalMultiUse`.  Ces classes sont semblables aux méthodes de niveau de module dans les classes [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)].  Visual Basic 6.0 et les versions antérieures créent implicitement des instances de ces objets pour vous la première fois que vous appelez l'une de leurs méthodes.  Par exemple, dans Visual Basic 6.0, vous pouvez ajouter une référence à la bibliothèque d'objets Microsoft DAO 3.6 et appeler la méthode `DBEngine` sans créer d'instance au préalable :  
  
```  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] exige que vous créiez toujours des instances d'objets COM pour pouvoir utiliser leurs méthodes.  Pour employer ces méthodes dans [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)], déclarez une variable de la classe voulue et assignez l'objet à la variable objet à l'aide du mot clé New.  Vous pouvez utiliser le mot clé `Shared` pour vous assurer qu'une seule instance de la classe est créée.  
  
 [!code-vb[VbVbalrInterop#23](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#23)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a> Erreurs non gérées dans les gestionnaires d'événements  
 L'un des problèmes courants d'interopérabilité concerne les erreurs dans les gestionnaires d'événements qui gèrent les événements déclenchés par des objets COM.  Ces erreurs sont ignorées, sauf si vous les recherchez spécifiquement à l'aide d'instructions `On Error` ou `Try...Catch...Finally`.  L'exemple suivant est extrait d'un projet [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] qui fait référence à l'objet COM de la bibliothèque Microsoft ActiveX Data Objects 2.8.  
  
 [!code-vb[VbVbalrInterop#24](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#24)]  
  
 Cet exemple génère une erreur comme prévu.  Cependant, si vous essayez le même exemple sans le bloc `Try...Catch...Finally`, 'erreur est ignorée comme si vous utilisiez l'instruction `OnError Resume Next`.  Sans la gestion des erreurs, la division par zéro échoue silencieusement.  Étant donné que ces erreurs ne déclenchent jamais d'erreur de type exception non gérée, il est important que vous utilisiez un certain mode de gestion des exceptions dans les gestionnaires d'événements qui gèrent les événements provenant des objets COM.  
  
### Compréhension des erreurs COM Interop  
 Sans la gestion des erreurs, les appels Interop génèrent souvent des erreurs qui fournissent peu d'informations.  Autant que possible, utilisez la gestion structurée des erreurs pour fournir de plus amples informations sur les problèmes lorsque ceux\-ci se produisent.  Cela peut être particulièrement utile lorsque vous déboguez des applications.  Par exemple :  
  
 [!code-vb[VbVbalrInterop#25](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#25)]  
  
 Vous pouvez obtenir des informations telles que la description des erreurs, les valeurs HRESULT et la source des erreurs COM par l'examen du contenu de l'objet exception.  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a> Problèmes liés aux contrôles ActiveX  
 La plupart des contrôles ActiveX qui fonctionnent avec Visual Basic 6.0 acceptent [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] sans problème.  Les principales exceptions sont les contrôles conteneur, des contrôles qui contiennent visuellement d'autres contrôles.  Voici quelques exemples d'anciens contrôles qui ne fonctionnent pas correctement avec [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] :  
  
-   le contrôle Frame de Microsoft Forms 2.0 ;  
  
-   le contrôle Up\-Down, également désigné contrôle Spin ;  
  
-   le contrôle Sheridan Tab.  
  
 Il n'existe que peu de solutions aux problèmes des contrôles ActiveX non pris en charge.  Vous pouvez faire migrer les contrôles existants vers [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] si vous possédez le code source d'origine.  Sinon, vous pouvez rechercher auprès des fournisseurs de logiciels les versions de contrôles actualisées compatibles avec .NET pour remplacer les contrôles ActiveX non pris en charge.  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a> Transmission des propriétés ReadOnly de contrôles avec ByRef  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] génère parfois des erreurs COM \(par exemple, "Error 0x800A017F CTL\_E\_SETNOTSUPPORTED"\) lorsque vous tentez de transmettre à d'autres procédures les propriétés `ReadOnly` de certains anciens contrôles ActiveX sous forme de paramètres `ByRef`.  Des appels de procédure similaires à partir de Visual Basic 6.0 ne génèrent pas d'erreur et les paramètres sont traités comme si vous les transmettiez par valeur.  Le message d'erreur que vous visualisez dans [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] correspond à l'objet COM qui signale que vous tentez de modifier une propriété sans procédure de propriété `Set`.  
  
 Si vous avez accès à la procédure qui est en cours d'appel, vous pouvez éviter cette erreur en employant le mot clé `ByVal` pour déclarer des paramètres qui acceptent les propriétés `ReadOnly`.  Par exemple :  
  
 [!code-vb[VbVbalrInterop#26](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#26)]  
  
 Si vous n'avez pas accès au code source de la procédure qui est en cours d'appel, vous pouvez forcer la transmission de la propriété par valeur. Pour ce faire, encadrez la procédure appelante d'une paire de crochets supplémentaires.  Par exemple, dans un projet qui fait référence à l'objet COM de la bibliothèque Microsoft ActiveX Data Objects 2.8, vous pouvez utiliser :  
  
 [!code-vb[VbVbalrInterop#27](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#27)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a> Déploiement d'assemblys exposant l'interopérabilité  
 Le déploiement d'assemblys exposant des interfaces COM soulève des défis uniques.  Ainsi, un problème potentiel se pose lorsque des applications distinctes référencent le même assembly COM.  Cette situation est courante lorsqu'une nouvelle version d'un assembly est installée et qu'une autre application continue d'utiliser l'ancienne version de l'assembly.  Si vous désinstallez un assembly partageant une DLL, vous pouvez involontairement rendre cette DLL indisponible aux autres assemblys.  
  
 Pour éviter ce problème, vous devez installer les assemblys partagés dans le Global Assembly Cache \(GAC\) et utiliser un module de fusion pour le composant.  Si vous ne pouvez pas installer l'application dans le GAC, vous devez l'installer dans un sous\-répertoire spécifique à la version du répertoire CommonFilesFolder.  
  
 Les assemblys qui ne sont pas partagés doivent être placés côte à côte dans le répertoire avec l'application appelante.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [Tlbexp.exe \(Type Library Exporter\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Global Assembly Cache](../Topic/Global%20Assembly%20Cache.md)