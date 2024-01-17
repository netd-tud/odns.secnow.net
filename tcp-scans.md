---
layout: base
title:  "Transparent DNS Forwarders Measurement Results for DNS over TCP Scans"
datatable: true
---


<script src="tcp_last_scan.js"></script>

<main id="last_scan" class="row row-cols-sm-1 px-3 mb-3 mt-5">
    <div class="box h-100 w-100">
        <div class="box-title">Scanning Continues</div>
            <div class="row px-3 mb-3 align-items-stretch">
                <div class="col-sm-12">
                    <p class="fs-4 text-justify">
                    Last successfull measurement: <b><u><script type="text/javascript">document.write(last_scan)</script></u></b>
                    </p>
                </div>
            </div>
    </div>
</main>



<main id="odns_components" class="row row-cols-sm-1 px-3 mb-3 mt-5">
    <div class="box h-100 w-100">
        <div class="box-title">Distribution of ODNS Components Worldwide</div>
            <div class="row px-3 mb-3 align-items-stretch">
                <div class="col-sm-12">
                    <iframe src="/assets/interactive_plots/tcp_worldmap_scan_overview.html" height="550" width="100%" scrolling="no"></iframe>
                </div>
            </div>
    </div>
</main>


<main id="odns_amount_over_time" class="row row-cols-sm-1 px-3 mb-3 mt-5">
    <div class="box h-100 w-100">
        <div class="box-title">Number of ODNS Components</div>
            <div class="row px-3 mb-3 align-items-stretch">
                <div class="col-sm-12">
                    <iframe src="/assets/interactive_plots/tcp_lineplot_scan_overview.html" height="420" width="100%" scrolling="no"></iframe>
                </div>
            </div>
    </div>
</main>


<main id="bars_topxcc" class="row row-cols-sm-1 px-3 mb-3 mt-5">
    <div class="box h-100 w-100">
        <div class="box-title">Share of ODNS Components of Top-50 Countries</div>
            <div class="row px-3 mb-3 align-items-stretch">
                <div class="col-sm-12">
                    <p class="fs-4 text-justify">
                    This plot shows the Top-50 countries which host the most transparent forwarders (absolut). The bars show the share of all ODNS components per country, the left y-axis shows the absolut amount of transparent forwarders active in these countries. Countries marked with a '*' are emerging markets.
                    </p>
                    <iframe src="/assets/interactive_plots/tcp_barplot_topxcc.html" height="420" width="100%" scrolling="no"></iframe>
                </div>
            </div>
    </div>
</main>

<main id="heatmap_topxcc" class="row row-cols-sm-1 px-3 mb-3 mt-5">
    <div class="box h-100 w-100">
        <div class="box-title">Consolidation Effect of Transparent Forwarders in Top-50 Countries</div>
            <div class="row px-3 mb-3 align-items-stretch">
                <div class="col-sm-12">
                    <p class="fs-4 text-justify">
                    This plot shows the Top-50 countries which host the most transparent forwarders (absolut). Countries marked with a '*' are emerging markets, the heatmap shows where transparent forwarders relay their requests to.
                    </p>
                    <iframe src="/assets/interactive_plots/tcp_heatmap_topxcc.html" height="420" width="100%" scrolling="no"></iframe>
                </div>
            </div>
    </div>
</main>