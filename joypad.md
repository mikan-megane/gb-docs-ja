# 🎮 ジョイパッド

## 🧮 FF00 - P1/JOYP - ジョイパッドレジスタ (R/W)

ゲームボーイの8つのアクションボタンと方向ボタンは、2x4のマトリクス状に配置されています。アクションボタンは`A`,`B`,`Start`,`Select`のことで、方向ボタンは俗に言う十字キーのことです。

このレジスタのbit5,4に書き込むことで、アクションボタンか方向ボタンかを選択し、bit0-3を読み出します。

```
Bit 7: 不使用
Bit 6: 不使用
Bit 5: P15 Select Action buttons    (0=Select)
Bit 4: P14 Select Direction buttons (0=Select)
Bit 3: P13 Input: Down  or Start    (0=Pressed) (読み取り専用)
Bit 2: P12 Input: Up    or Select   (0=Pressed) (読み取り専用)
Bit 1: P11 Input: Left  or B        (0=Pressed) (読み取り専用)
Bit 0: P10 Input: Right or A        (0=Pressed) (読み取り専用)
```

**注意**

ほとんどのゲームプログラムは、このポートから何度も連続して読み込みを行っています。
最初に読み込まれた値は、入力が安定するまでの短い遅延として使用され、最後に読み込まれた値のみが実際に使用されます。

## 💡 SGBでのジョイパッドの特殊な使い道

通常のジョイパッド入力の他に、SGB対応のゲームではジョイパッドレジスタを悪用してSGBコマンドパケットをスーファミへ出力したり、スーファミに接続可能な最大4つのジョイパッドからゲームパッドの状態を読み取ったりすることができます。詳しくはSGBのページをご覧ください。