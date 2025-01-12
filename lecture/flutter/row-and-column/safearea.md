# SafeArea

* 확실하게 widget들이 나타나는 영역에 표시하게 만드는 widget
* 둥근 모서리, 상태바등을 피해서 영역이 설정 됨

<pre class="language-dart"><code class="lang-dart">const colors = [
  Colors.red,
  Colors.orange,
  Colors.yellow,
  Colors.green,
];

<strong>      body: SafeArea(
</strong>        child: Container(
          color: Colors.black,
          child: Column(
            children: colors.map((e) => Container(
              height: 50,
                width: 50,
                color: e,
            )).toList(),
          ),
        ),
      ),
</code></pre>

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
