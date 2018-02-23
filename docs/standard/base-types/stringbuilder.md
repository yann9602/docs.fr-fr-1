---
title: "À l’aide de la classe StringBuilder Class dans .NET"
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
- cpp
helpviewer_keywords:
- Remove method
- strings [.NET Framework], capacities
- StringBuilder object
- Replace method
- AppendFormat method
- Append method
- Insert method
- strings [.NET Framework], StringBuilder object
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3a6c8f6dee9f2a1da6ed4a8219c1b4832464d9aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-stringbuilder-class-in-net"></a>À l’aide de la classe StringBuilder Class dans .NET
Le type <xref:System.String> est immuable. Chaque fois que vous utilisez une des méthodes du type <xref:System.String?displayProperty=nameWithType> (classe), vous créez un nouvel objet string en mémoire, ce qui requiert une nouvelle allocation d’espace pour ce nouvel objet. Dans les situations où vous avez besoin pour effectuer des modifications répétées d’une chaîne, la surcharge associée de création d’un nouveau <xref:System.String> objet peut s’avérer coûteux. La classe <xref:System.Text.StringBuilder?displayProperty=nameWithType> peut être utilisée lorsque vous souhaitez modifier une chaîne sans créer un nouvel objet. A l’aide de la classe <xref:System.Text.StringBuilder>  vous pouvez améliorer les performances lors de la concaténation de plusieurs chaînes dans une boucle.  
  
## <a name="importing-the-systemtext-namespace"></a>Importation de l’espace de noms System.Text  
 La classe <xref:System.Text.StringBuilder>  se trouve dans l'espace de noms  <xref:System.Text>.  Pour éviter d’avoir à fournir l'espace de noms complet dans votre code, vous pouvez importer <xref:System.Text>.
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Instanciation d’un objet StringBuilder  
 Vous pouvez créer une nouvelle instance de la classe <xref:System.Text.StringBuilder> en initialisant votre variable avec l’une des méthodes de constructeur surchargées, comme illustré dans l’exemple suivant.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Définition de la capacité et de la longueur  
 Bien que le <xref:System.Text.StringBuilder> est un objet dynamique qui vous permet d’augmenter le nombre de caractères dans la chaîne qu’il encapsule, vous pouvez spécifier une valeur pour le nombre maximal de caractères qu’elle peut contenir. Cette valeur est appelée la capacité de l’objet et ne doit pas être confondue avec la longueur de la chaîne qui en cours <xref:System.Text.StringBuilder> contient. Par exemple, vous pouvez créer une nouvelle instance de la <xref:System.Text.StringBuilder> classe avec la chaîne « Hello », qui a une longueur de 5 et vous pouvez spécifier que l’objet a une capacité maximale de 25. Lorsque vous modifiez le <xref:System.Text.StringBuilder>, il ne se réalloue pas une taille pour lui-même jusqu'à ce que la capacité est atteinte. Quand cela se produit, le nouvel espace est alloué automatiquement et la capacité est doublée. Vous pouvez spécifier la capacité de le <xref:System.Text.StringBuilder> à l’aide d’un des constructeurs surchargés de la classe. L’exemple suivant spécifie que l’objet `MyStringBuilder` peut être développé en 25 espaces, au maximum.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 En outre, vous pouvez utiliser la lecture/écriture <xref:System.Text.StringBuilder.Capacity%2A> propriété pour définir la longueur maximale de votre objet. L’exemple suivant utilise la propriété **Capacity** pour définir la longueur maximale de l’objet.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 Le <xref:System.Text.StringBuilder.EnsureCapacity%2A> méthode peut être utilisée pour vérifier la capacité d’actuel **StringBuilder**. Si la capacité est supérieure à la valeur passée, aucune modification n’est apportée ; en revanche, si la capacité est inférieure à la valeur passée, la capacité actuelle est modifiée pour correspondre à la valeur passée.  
  
 Le <xref:System.Text.StringBuilder.Length%2A> propriété peut également être affichée ou définie. Si vous attribuez à la propriété **Length** une valeur supérieure à celle de la propriété **Capacity**, la propriété **Capacity** prend automatiquement la valeur de la propriété **Length**. Si vous attribuez à la propriété **Length** une valeur inférieure à la longueur de la chaîne dans l’instance actuelle de **StringBuilder**, la chaîne se raccourcit.  
  
## <a name="modifying-the-stringbuilder-string"></a>Modification de la chaîne StringBuilder  
 Le tableau suivant répertorie les méthodes que vous pouvez utiliser pour modifier le contenu d’une instance de **StringBuilder**.  
  
|Nom de la méthode|Utilisation|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Ajoute des informations à la fin de l’instance actuelle de **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Remplace un spécificateur de format passé dans une chaîne avec du texte mis en forme.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Insère une chaîne ou un objet dans l’index spécifié de l’instance actuelle de **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Supprime un nombre de caractères spécifié de l’instance actuelle de **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Remplace un caractère spécifié au niveau d’un index spécifié.|  
  
### <a name="append"></a>Append  
 Le **Append** méthode peut être utilisée pour ajouter du texte ou une représentation de chaîne d’un objet à la fin d’une chaîne représentée par le **StringBuilder**. L’exemple suivant initialise une instance de **StringBuilder** à « Hello World » avant d’ajouter du texte à la fin de l’objet. L’espace est alloué automatiquement en fonction des besoins.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 Le <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> méthode ajoute du texte à la fin de la <xref:System.Text.StringBuilder> objet. Il prend en charge la fonctionnalité de mise en forme composite (pour plus d’informations, consultez [mise en forme Composite](../../../docs/standard/base-types/composite-formatting.md)) en appelant le <xref:System.IFormattable> implémentation de l’objet ou les objets à mettre en forme. Par conséquent, elle accepte les chaînes de format standard pour les valeurs numériques, de date et d’heure et d’énumération, les chaînes de format personnalisé pour les valeurs numériques et de date et d’heure, ainsi que les chaînes de format définies pour des types personnalisés. (Pour plus d’informations sur la mise en forme, consultez [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md).) Vous pouvez utiliser cette méthode pour personnaliser le format des variables et ajouter ces valeurs à un <xref:System.Text.StringBuilder>. L’exemple suivant utilise le <xref:System.Text.StringBuilder.AppendFormat%2A> méthode pour placer une valeur entière mise en forme en tant que valeur monétaire à la fin d’un <xref:System.Text.StringBuilder> objet.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Insert  
 Le <xref:System.Text.StringBuilder.Insert%2A> méthode ajoute une chaîne ou un objet à une position spécifiée dans le courant <xref:System.Text.StringBuilder> objet. L’exemple suivant utilise cette méthode pour insérer un mot à la sixième position d’un <xref:System.Text.StringBuilder> objet.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Remove  
 Vous pouvez utiliser la **supprimer** méthode pour supprimer un nombre spécifié de caractères à partir du <xref:System.Text.StringBuilder> objet, en commençant à un index de base zéro spécifié. L’exemple suivant utilise le **supprimer** méthode pour raccourcir un <xref:System.Text.StringBuilder> objet.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>Remplacer  
 Le **remplacer** méthode peut être utilisée pour remplacer des caractères dans le <xref:System.Text.StringBuilder> objet avec un autre caractère de spécifié. L’exemple suivant utilise le **remplacer** méthode pour rechercher un <xref:System.Text.StringBuilder> pour toutes les instances de point d’exclamation ( !) de caractères et les remplacement par le caractère point d’interrogation ( ?) de l’objet.  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Conversion d’un objet StringBuilder en chaîne  
 Vous devez convertir le <xref:System.Text.StringBuilder> de l’objet à un <xref:System.String> avant de pouvoir passer la chaîne représentée par l’objet le <xref:System.Text.StringBuilder> objet à une méthode qui a un <xref:System.String> paramètre ou bien l’afficher dans l’interface utilisateur. Effectuer cette conversion en appelant le <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> (méthode). L’exemple suivant appelle un certain nombre de <xref:System.Text.StringBuilder> méthodes, puis appelle la <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> méthode pour afficher la chaîne.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
 [Opérations de chaînes de base](../../../docs/standard/base-types/basic-string-operations.md)  
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)
