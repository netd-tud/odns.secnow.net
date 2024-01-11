---
layout: base
title:  "Home"
subtitle: "Synopsis"
---

<main id="Note" class="row row-cols-sm-1 px-3 mb-3 mt-5">
    <div class="box h-100 w-100">
        <div class="box-title">New Measurements</div>
        <div class="row px-3 mb-3 align-items-stretch">
            <div class="col-sm-12">
                <p class="fs-3 text-justify">
                We started to continue our measurements on a weekly base!<br>Click <a href="/data">here</a> to see our current DNS over <b>UDP</b> results.<br>Or <a href="/tcp-scans">here</a> to see our current DNS over <b>TCP</b> results.
                </p>
            </div>
        </div>
    </div>
</main>

<main id="Home" class="row row-cols-sm-1 px-3 mb-3 mt-5">
    <div class="box h-100 w-100">
        <div class="box-title">Synopsis</div>
        <div class="row row-cols-lg-1 row-cols-xl-2 px-3 mb-3 align-items-stretch">
            <div class="col-sm-12">
                            <p class="fs-3 text-justify">
                                We revisit the <u class="primary">open DNS (ODNS) infrastructure</u> and, for the first time, systematically measure and analyze  <u class="success">transparent forwarders</u>, DNS components that <u class="danger">transparently relay</u> between stub resolvers and recursive resolvers. We introduce <u class="success">DNSRoute++</u>, a new traceroute approach that leverages the behaviour of transparent forwarders and explores interconnectivity in the ODNS.
                                
                            </p>
                <div id="goto-reports">
                    <a href="/data" class="text-decoration-none link-dark">
                        <hr>
                        <p class="text-center">
                            <strong class="fs-2">
                                           Key findings include that transparent forwarders contribute 26% to the current ODNS infrastructure, missed by common scanning campaigns; and that many transparent forwarders relay to a few selected public resolvers such as Google and Cloudflare, which confirms a consolidation trend of DNS stakeholders. Full access to data will follow soon. <!--<u class="primary">assurance profiles here</u>-->

                            </strong>
                        </p>
                        <hr>
                    </a>
                </div>
            </div>
            <div class="col-sm-12">
                <a href="/assets/static/nksw-tfuco-21.pdf"><img src="/assets/img/main.jpg" class="w-100"></a>
            </div>
        </div>
    </div>
</main>
