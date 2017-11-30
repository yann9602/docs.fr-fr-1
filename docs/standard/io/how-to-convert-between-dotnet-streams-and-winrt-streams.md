---
title: "Comment : effectuer une conversion entre les flux .NET Framework et les flux Windows Runtime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11c22bf71109137ea328b8e1136180494364ce0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-between-net-framework-streams-and-windows-runtime-streams"></a>Comment : effectuer une conversion entre les flux .NET Framework et les flux Windows Runtime
Le .Net Framework pour les applications Windows Store est un sous-ensemble du .NET Framework complet. En raison de la sécurité et d'autres spécifications des applications Windows Store, vous ne pouvez pas utiliser l'ensemble d'API .NET Framework pour ouvrir et lire des fichiers. Pour plus d’informations, consultez [Vue d’ensemble de .NET pour les applications du Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx). Toutefois, vous pouvez utiliser des API .NET Framework pour les autres opérations de manipulation des flux. Pour manipuler ces flux, il peut s’avérer nécessaire d’effectuer une conversion entre un type de flux .NET Framework tel que <xref:System.IO.MemoryStream> ou <xref:System.IO.FileStream>, et un flux Windows Runtime tel que [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx), [IOutputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx)ou [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx).  
  
 La classe <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` contient des méthodes qui rendent ces conversions plus faciles. Toutefois, il existe des différences sous-jacentes entre les flux .NET Framework et Windows Runtime qui affecteront les résultats obtenus lors de l'utilisation ces méthodes. Ces différentes sont décrites en détail dans les sections suivantes.  
  
<a name="BKMK_ConvertingfromaWindowsRuntimestreamtoaNETFrameworkstream"></a>   
## <a name="converting-from-a-windows-runtime-stream-to-a-net-framework-stream"></a>Conversion d'un flux Windows Runtime en un flux .NET Framework  
 Convertissez un flux Windows Runtime en un flux .NET Framework en utilisant l'une des méthodes <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` suivantes :  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream`  
 Convertit un flux d'accès aléatoire Windows Runtime en un flux managé du sous-ensemble .NET pour les applications du Windows Store.  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite`
 Convertit un flux de sortie Windows Runtime en un flux managé du sous-ensemble .NET pour les applications du Windows Store.  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead`  
 Convertit un flux d'entrée Windows Runtime en un flux managé du sous-ensemble .NET pour les applications du Windows Store.  
  
 Le Windows Runtime offre des types de flux qui prennent en charge la lecture seule, l'écriture seule ou la lecture et l'écriture. Ces capacités sont conservées lorsque vous convertissez un flux Windows Runtime en un flux .NET Framework. En outre, si vous convertissez un flux Windows Runtime en un flux .NET Framework et inversement, vous obtenez l'instance du Windows Runtime en retour. Il est recommandé d'utiliser la méthode de conversion correspondant aux capacités du flux Windows Runtime que vous souhaitez convertir. Toutefois, comme [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) est accessible en lecture et en écriture (il implémente [IOutputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx) et [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx)), vous pouvez utiliser n’importe quelle méthode de conversion. Par ailleurs, les capacités du flux d’origine sont conservées. Par exemple, l’utilisation de <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead` pour convertir [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) n’empêche pas le flux .NET Framework converti d’être accessible en lecture seule. Il est également accessible en écriture.  
  
#### <a name="to-convert-from-a-windows-runtime-random-access-stream-to-a-net-framework-stream"></a>Pour convertir un flux d'accès aléatoire Windows Runtime en un flux .NET Framework  
  
-   Utilisez la méthode <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream` .  
  
     L'exemple de code suivant montre comment inviter l'utilisateur à sélectionner un fichier, l'ouvrir avec les API Windows Runtime, puis le convertir en un flux .NET Framework, qui est lu et envoyé vers un bloc de texte. Dans ce scénario, vous manipulez généralement le flux avec les API .NET Framework avant de sortir les résultats.  
  
     Pour exécuter cet exemple, vous devez créer une application XAML Windows Store, contenant un bloc de texte nommé `TextBlock1` et un bouton nommé  `Button1`. L'événement Click du bouton doit être associé à la méthode `button1_Click` illustrée dans l'exemple.  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#1)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#1)]  
  
<a name="BKMK_ConvertingfromaNETFrameworkstreamtoaWindowsRuntimestream"></a>   
## <a name="converting-from-a-net-framework-stream-to-a-windows-runtime-stream"></a>Conversion d'un flux .NET Framework en un flux Windows Runtime  
 Convertissez un flux .NET Framework en un flux Windows Runtime en utilisant l'une des méthodes <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` suivantes :  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream`  
 Convertit un flux managé du sous-ensemble .NET pour les applications du Windows Store en un flux d'entrée Windows Runtime.  
  
<!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A>  --> `System.IO.WindowsRuntimeStreamExtensions.AsOutputStream`
 Convertit un flux managé du sous-ensemble .NET pour les applications du Windows Store en un flux de sortie Windows Runtime.  
  
 [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md)  
 Convertit un flux managé du sous-ensemble .NET pour les applications du Windows Store en un flux d'accès aléatoire qui peut être utilisé pour lire ou écrire dans le Windows Runtime.  
  
 Lorsque vous convertissez un flux .NET Framework en un flux Windows Runtime, les capacités du flux converti dépendent du flux d'origine. Par exemple, si le flux d'origine prend en charge la lecture et l'écriture, et que vous appelez <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream` pour convertir le flux, le type retourné est un `IRandomAccessStream`qui implémente  `IInputStream` et `IOutputStream`et prend en charge la lecture et l'écriture.  
  
 Les flux .NET Framework ne prennent pas en charge le clonage, même après la conversion. Cela signifie que si vous convertissez un flux .NET Framework en flux Windows Runtime, et si vous appelez [GetInputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.inmemoryrandomaccessstream.getinputstreamat.aspx) ou [GetOutputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.getoutputstreamat.aspx), qui appellent [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) , ou si vous appelez [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) directement, une exception est levée.  
  
#### <a name="to-convert-from-a-net-framework-stream-to-a-windows-runtime-random-access-stream"></a>Pour convertir un flux .NET Framework en un flux d'accès aléatoire Windows Runtime  
  
-   Utilisez la méthode [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) , comme illustré dans l'exemple suivant.  
  
    > [!IMPORTANT]
    >  Assurez-vous que le flux du .NET Framework que vous utilisez prend en charge la recherche, ou copiez-le dans un flux qui la prend en charge. Vous pouvez utiliser la propriété <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> pour le déterminer.  
  
     Pour exécuter cet exemple, vous devez créer une application XAML Windows Store qui cible le .NET Framework 4.5.1 et contient un bloc de texte nommé `TextBlock2` et un bouton nommé `Button2`. L'événement Click du bouton doit être associé à la méthode `button2_Click` illustrée dans cet exemple.  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#2)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage rapide : Lecture et écriture dans un fichier (Windows)](http://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
 [Vue d’ensemble des applications .NET pour le Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [.NET pour les applications du Windows Store : API prises en charge](http://msdn.microsoft.com/library/windows/apps/br230232.aspx)
