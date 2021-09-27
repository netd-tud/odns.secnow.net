---
layout: base
title:  "Transparent DNS Forwarders Measurement Results"
datatable: true
---

<main id="data" class="row row-cols-sm-1 px-3 mb-3 mt-5">
    <div class="box h-100 w-100">
      <div class="box-title">Measurement Results</div>
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
