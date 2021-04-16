<head>
<script>
(function () {
    var mathconfig = document.createElement("script");
    mathconfig.type = "text/x-mathjax-config";
    mathconfig.text = [
        "MathJax.Hub.Config({",
            "extensions: ['tex2jax.js'],",
            "jax: ['input/TeX', 'output/HTML-CSS'],",
            "tex2jax: {",
                "inlineMath: [ ['$','$'], ['\\\\(','\\\\)'] ],",
                "displayMath: [ ['$$','$$'], ['\\\\[','\\\\]'] ],",
                "processEscapes: true",
            "},",
            "'HTML-CSS': { availableFonts: ['TeX'] }",
        "});"
    ].join("\n");
    var mathparent = (document.head || document.body || document.documentElement);
    mathparent.appendChild(mathconfig);
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src  = "http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML";
    var parent = (document.head || document.body || document.documentElement);
    parent.appendChild(script);
})();
</script>
</head>
