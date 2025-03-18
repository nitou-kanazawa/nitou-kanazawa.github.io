---
title: SharpLab
categories: [C#]
tags:
  - C#
  - .NET
  - IL
---

## 概要

[SharpLab][SharpLab]は.NETのWeb Playground．コンパイル結果や IL（Intermediate Language）、JIT の最適化後のアセンブリコードを確認できる．

[リポジトリ](https://github.com/ashmind/SharpLab)


## 使用例

例えば以下のような`foreach`を使ったループは`IEnumerator`での走査に書き換えられていることが分かる．（ちなみに`sequence`を`IEnumerable`ではなく普通に配列に格納した場合は，最適化で`for`でのアクセスに展開される）

[リンク](https://sharplab.io/#v2:CYLg1APgAgDABFAjAbgLACgNQMwIEwKIDscA3hnJQrlACxwCyAhgJYB2AFAJRkVX/sALnADKARwCuTAE4BTDkLhsJAWx4BeAHxLVcAFQ6VaTOn4C2wwSxWy46uHmNmqigCrXZAZwUXDG7VY2+oZOznB8zkgAnBziUnIceFxcoZGIMe423tjJxgCQAL4YBUA=)

**元のC#コード**
```cs
using System;
using System.Collections.Generic;

public class Program {
    
    public IEnumerable<int> sequence = new int[] {1, 3, 4, 5};
    
    public void Main() {
        
        foreach(var data in sequence){
            Console.WriteLine(data);
        }
	}
}
```

**ILからでコンパイルされたC#コード**
```cs
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Reflection;
using System.Runtime.CompilerServices;
using System.Runtime.InteropServices;
using System.Security;
using System.Security.Permissions;

[assembly: CompilationRelaxations(8)]
[assembly: RuntimeCompatibility(WrapNonExceptionThrows = true)]
[assembly: Debuggable(DebuggableAttribute.DebuggingModes.Default | DebuggableAttribute.DebuggingModes.IgnoreSymbolStoreSequencePoints | DebuggableAttribute.DebuggingModes.EnableEditAndContinue | DebuggableAttribute.DebuggingModes.DisableOptimizations)]
[assembly: SecurityPermission(SecurityAction.RequestMinimum, SkipVerification = true)]
[assembly: AssemblyVersion("0.0.0.0")]
[module: UnverifiableCode]
[module: RefSafetyRules(11)]
public class Program {
    [Nullable(1)]
    public IEnumerable<int> sequence;

    public void Main() {
        IEnumerator<int> enumerator = sequence.GetEnumerator();
        try {
            while (enumerator.MoveNext()) {
                int current = enumerator.Current;
                Console.WriteLine(current);
            }
        }
        finally {
            if (enumerator != null)
            {
                enumerator.Dispose();
            }
        }
    }

    public Program() {
        int[] array = new int[4];
        RuntimeHelpers.InitializeArray(array, (RuntimeFieldHandle)/*OpCode not supported: LdMemberToken*/);
        sequence = array;
        base..ctor();
    }
}

[CompilerGenerated]
internal sealed class <PrivateImplementationDetails> {
    [StructLayout(LayoutKind.Explicit, Pack = 1, Size = 16)]
    internal struct __StaticArrayInitTypeSize=16
    {
    }

    internal static readonly __StaticArrayInitTypeSize=16 41B55B4DEDC66ED3C584B40C7DCC5A513748CD552A48FD9D46DF0BFC87E57152/* Not supported: data(01 00 00 00 03 00 00 00 04 00 00 00 05 00 00 00) */;
}
```


## 参考記事

- [qiita: C#で手軽にILや内部を確認するなら「SharpLab」！](https://qiita.com/RyotaMurohoshi/items/a6a252915f11f7559efe)
- [はなちる: C#の中間言語ILを読めるようになりたい(SharpLabの紹介)](https://www.hanachiru-blog.com/entry/2021/07/27/152200)
- [ソフトライム: SharpLabを使ったC#のメモリ管理の確認](https://soft-rime.com/post-9359/)
- [hatena: sharplab-inspect の使い方](https://shikaku-sh.hatenablog.com/entry/c-sharp-how-to-use-sharplab-inspect)


<!-- リンク -->

[SharpLab]: https://sharplab.io/
