---
layout: base
title:  "Transparent DNS Forwarders Measurement Results"
datatable: true
---

<script src="last_scan.js"></script>

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
        <div class="box-title">Distribution of ODNS Components over the World</div>
            <div class="row px-3 mb-3 align-items-stretch">
                <div class="col-sm-12">
                    <iframe src="/assets/interactive_plots/worldmap_scan_overview.html" height="550" width="100%" scrolling="no"></iframe>
                </div>
            </div>
    </div>
</main>


<main id="odns_amount_over_time" class="row row-cols-sm-1 px-3 mb-3 mt-5">
    <div class="box h-100 w-100">
        <div class="box-title">Number of ODNS Components</div>
            <div class="row px-3 mb-3 align-items-stretch">
                <div class="col-sm-12">
                    <iframe src="/assets/interactive_plots/lineplot_scan_overview.html" height="420" width="100%" scrolling="no"></iframe>
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
                    This plot shows the Top-50 countries which host the most transparent forwarders (absolut). The bars show the share of all ODNS components per country, the left y-axis shows the absolut amount of transparent forwarders active in these countries. Countries highlighted in bold and marked with a '*' are emerging markets.
                    </p>
                    <iframe src="/assets/interactive_plots/barplot_topxcc.html" height="550" width="100%" scrolling="no"></iframe>
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
                    This plot shows the Top-50 countries which host the most transparent forwarders (absolut). Countries highlighted in bold and marked with a '*' are emerging markets. This heatmap shows where transparent forwarders relay their requests to. Most of the requests are forwarded to resolver of Google. 
                    </p>
                    <img src="/assets/img/figures/heatmap_dominance_pub_rr.png" width="90%">
                </div>
            </div>
    </div>
</main>


<main id="data" class="row row-cols-sm-1 px-3 mb-3 mt-5">
    <div class="box h-100 w-100">
      <div class="box-title">Top 50 Autonomous System with most Transparent Forwarders</div>
      <div class="row px-3 mb-3 align-items-stretch">
        <div class="col-sm-12">
          <p class="fs-4 text-justify">
          This table shows the top-50 autonomous systems (AS) that host most of the transparent DNS forwarders as presented in the ACM CoNEXT'21 paper. The <a href="https://github.com/ilabrg/artifacts-conext21-dns-fwd/tree/main/dns-measurement-analysis/dataframes">full data set</a> is also available as part of the <a href="https://github.com/ilabrg/artifacts-conext21-dns-fwd">artifacts collection</a>.
          </p>

          <p class="fs-3 text-justify">

  <table id="table_id">
    {% for row in site.data.data %}
      {% if forloop.first %}
      <thead>
        <tr>
          {% for pair in row %}
            <th>{{ pair[0] }}</th>
          {% endfor %}
        </tr>
      </thead>
      {% endif %}

      {% if forloop.index == 1 %} <tbody>
      {% endif %}
        <tr>
          {% for pair in row %}
            <td>{{ pair[1] }}</td>
          {% endfor %}
        </tr>

    {% endfor %}
      </tbody>
  </table>

  <script>
  $(document).ready( function () {
      $('#table_id').DataTable();
  } );
  </script>

          </p>
        </div>
      </div>
    </div>

</main>
