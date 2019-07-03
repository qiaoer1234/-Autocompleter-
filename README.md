# -Autocompleter-
<div class="alert cjms" role="alert">插件描述：autocompleter是一个简单的，容易的，可定制的自动完成功能插件，支持缓存。</div>
<h3>使用方法：</h3><p><strong>添加引用</strong></p><p>最低要求：jquery.autocompleter.css和jquery.autocompleter.min.js。</p><p><br /></p><p><strong>脚本：</strong></p><pre class="brush:html;toolbar:false">&lt;script&nbsp;src=&quot;js/jquery.js&quot;&nbsp;type=&quot;text/javascript&quot;&gt;&lt;/script&gt;
&lt;script&nbsp;src=&quot;js/jquery.autocompleter.min.js&quot;&nbsp;type=&quot;text/javascript&quot;&gt;&lt;/script&gt;</pre><p><br /></p><p>样式：</p><pre class="brush:html;toolbar:false">&lt;link&nbsp;rel=&quot;stylesheet&quot;&nbsp;href=&quot;css/jquery.autocompleter.css&quot;&gt;</pre><p><br /></p><p>定义你的autocompleter：</p><pre class="brush:js;toolbar:false">$(function&nbsp;()&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;$(&#39;input&#39;).autocompleter({&nbsp;source:&nbsp;&#39;path/to/get_data_request&#39;&nbsp;});
});</pre><p><br /></p><p>或用于本地JSON来源：</p><pre class="brush:js;toolbar:false">var&nbsp;data&nbsp;=&nbsp;[
&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;&quot;value&quot;:&nbsp;&quot;1&quot;,&nbsp;&quot;label&quot;:&nbsp;&quot;one&quot;&nbsp;},
&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;&quot;value&quot;:&nbsp;&quot;2&quot;,&nbsp;&quot;label&quot;:&nbsp;&quot;two&quot;&nbsp;},
&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;&quot;value&quot;:&nbsp;&quot;3&quot;,&nbsp;&quot;label&quot;:&nbsp;&quot;three&quot;&nbsp;}
];
$(function&nbsp;()&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;$(&#39;input&#39;).autocompleter({&nbsp;source:&nbsp;data&nbsp;});
});</pre><p>如果你不会在源对象定义了一个值，标签将被用作后选择在输入字段的默认值。</p><p><br /></p><h3>方法：</h3><p>插件后更改选项的定义：</p><pre class="brush:js;toolbar:false">$(&#39;#input&#39;).autocompleter(&#39;option&#39;,&nbsp;data);</pre><p><br /></p><p>例如：</p><pre class="brush:js;toolbar:false">$(&#39;#input&#39;).autocompleter(&#39;option&#39;,&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;limit:&nbsp;5,
&nbsp;&nbsp;&nbsp;&nbsp;template:&nbsp;&#39;&lt;img&nbsp;src=&quot;{{&nbsp;image&nbsp;}}&quot;&nbsp;alt=&quot;Image&nbsp;for&nbsp;autocompleter&nbsp;list&nbsp;item&quot;&nbsp;/&gt;&nbsp;{{&nbsp;label&nbsp;}}&#39;
});</pre><p><br /></p><p>开放列表：</p><pre class="brush:js;toolbar:false">$(&#39;#input&#39;).autocompleter(&#39;open&#39;);</pre><p><br /></p><p>关闭页面：</p><pre class="brush:js;toolbar:false">$(&#39;#input&#39;).autocompleter(&#39;close&#39;);</pre><p>摧毁插件：</p><pre class="brush:js;toolbar:false">$(&#39;#input&#39;).autocompleter(&#39;destroy&#39;);</pre><p><br /></p><p>清除所有缓存：</p><pre class="brush:js;toolbar:false">$.autocompleter(&#39;clearCache&#39;);</pre><p><br /></p><p>设置默认值：</p><pre class="brush:js;toolbar:false">$.autocompleter(&#39;defaults&#39;,&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;customClass:&nbsp;&#39;myClassForAutocompleter&#39;
});</pre><p><br /></p><p><strong>例如：</strong></p><p>Autocompleter第一名称输入缓存,匹配强调限制和5的结果。</p><p><br /></p><p>形式：</p><pre class="brush:html;toolbar:false">&lt;label&nbsp;for=&quot;gender_male&quot;&gt;Male&lt;/label&gt;
&lt;input&nbsp;type=&quot;radio&quot;&nbsp;name=&quot;gender&quot;&nbsp;value=&quot;male&quot;&nbsp;id=&quot;gender_male&quot;&nbsp;checked=&quot;checked&quot;&nbsp;/&gt;
&lt;label&nbsp;for=&quot;gender_female&quot;&gt;Female&lt;/label&gt;
&lt;input&nbsp;type=&quot;radio&quot;&nbsp;name=&quot;gender&quot;&nbsp;value=&quot;female&quot;&nbsp;id=&quot;gender_female&quot;&nbsp;/&gt;
&lt;label&nbsp;for=&quot;firstname&quot;&gt;First&nbsp;Name&lt;/label&gt;
&lt;input&nbsp;type=&quot;text&quot;&nbsp;name=&quot;firstname&quot;&nbsp;id=&quot;firstname&quot;&nbsp;/&gt;</pre><p><br /></p><p><strong>JavaScript：</strong></p><pre class="brush:js;toolbar:false">$(function&nbsp;()&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;$(&quot;#firstname&quot;).autocompleter({
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;limit:&nbsp;5,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;cache:&nbsp;true,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;combine:&nbsp;function&nbsp;()&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;var&nbsp;gender&nbsp;=&nbsp;$(&quot;input:radio[name=gender]:checked&quot;).val();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;gender:&nbsp;gender
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;};
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;callback:&nbsp;function&nbsp;(value,&nbsp;index)&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;console.log(&nbsp;&quot;Value&nbsp;&quot;+value+&quot;&nbsp;are&nbsp;selected&nbsp;(with&nbsp;index&nbsp;&quot;+index+&quot;).&quot;&nbsp;);
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
&nbsp;&nbsp;&nbsp;&nbsp;});
});</pre><p><br /></p><p><strong>主要结构：</strong></p><pre class="brush:html;toolbar:false">&lt;div&nbsp;class=&quot;autocompleter&quot;&nbsp;id=&quot;autocompleter-1&quot;&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;ul&nbsp;class=&quot;autocompleter-list&quot;&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li&nbsp;class=&quot;autocompleter-item&quot;&gt;First&lt;/li&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;li&nbsp;class=&quot;autocompleter-item&quot;&gt;Last&lt;/li&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/ul&gt;
&lt;/div&gt;</pre>
