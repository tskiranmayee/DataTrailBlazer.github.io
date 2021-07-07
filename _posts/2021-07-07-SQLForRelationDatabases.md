---
layout: post
title: SQL for Relation Databases
---

<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" type="text/css" href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.3.4/css/bootstrap.css"/>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.3.4/js/bootstrap.min.js"></script>
    <script src="ZeroClipboard.js"></script>
    <style>
        .btn-clipboard {
            position: relative;
            right: 51px;
            border-radius: 0 4px 0 4px;

        }
        .zeroclipboard-is-hover {
            color: #fff;
            border-color: #563d7c;
            background-color: #563d7c;
        }
    </style>
</head>
<body>
    <div class="container">
        <h5>your code</h5>
        <div class="row-fluid">
            <div class="code-box">
                <span class="btn btn-default btn-sm btn-clipboard pull-right" data-clipboard-target="code">
                    Copy
                </span>
                <pre id="code">
var odds = evens.map(v => v + 1);
var nums = evens.map((v, i) => v + i);
var pairs = evens.map(v => ({even: v, odd: v + 1}));
                </pre>
            </div>
        </div>
    </div>
</body>
<script>
    $(function () {
        // zeroclipboard object
        var clip = new ZeroClipboard($('.btn-clipboard'));
        var clipElems = $(clip.elements());
        // tooltip logic
        var tooltipOptions = {title: 'Copy to clipboard', placement: 'top'};
        clipElems.tooltip(tooltipOptions);
        clipElems.click(function() {
            clipElems.data('bs.tooltip').options.title = 'Copied!';
            clipElems.tooltip('show');
        });
        clipElems.mouseleave(function () {
            clipElems.data('bs.tooltip').options.title = tooltipOptions.title;
        });
    });
</script>
</html>

