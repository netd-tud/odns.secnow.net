const COMMONS = {
    pubsufmap: {
        gTLD: 'Generic Top-Level Domain',
        ccTLD: 'Country Code Top-Level Domain',
        ccSLD: 'Country Code Sponsored Domain',
        sTLD: 'Sponsored Top-Level Domain',

    },
    certtypemap: {
        DV: ['Domain Validation', 'warning'],
        OV: ['Organization Validation', 'success'],
        EV: ['Extended Validation', 'success'],
    },
    assurancemap: {
        good: 'border-success',
        bad: 'border-warning',
        ugly: 'border-danger'
    }
}

function getEl(selector) {
    return document.querySelector(selector);
}

function setInner(selector, inner) {
    let el = getEl(selector);
    el.innerHTML = inner;
    return el;
}

function toggleHide(selector, hide) {
    let el = getEl(selector);
    hide ? el.setAttribute('hidden', '') : el.removeAttribute('hidden');
    return el;
}

function bool(value) {
    return JSON.parse(value);
}

function cloneTemplate(selector) {
    return getEl(`template${selector}`).content.cloneNode(true);
}

function genIdSpec(dataset) {
    let restricted = ['ccSLD', 'sTLD'].includes(dataset.pubSufType);
    let goodCert = ['OV', 'EV'].includes(dataset.certType);
    let dnssec = bool(dataset.dnssec);

    let assurance;
    if (restricted && goodCert && dnssec) {
        assurance = 'good';
    } else if (goodCert || (restricted && dnssec && !goodCert)) {
        assurance = 'bad';
    } else {
        assurance = 'ugly';
    }

    let children = [];
    if (restricted) {
        children.push(cloneTemplate('#id-restricted-tld'));
    } else {
        children.push(cloneTemplate('#id-unrestricted-tld'));
    }

    if (goodCert) {
        children.push(cloneTemplate('#id-good-cert'));
    } else {
        children.push(cloneTemplate('#id-not-good-cert'));

        if (!dnssec) {
            children.push(cloneTemplate('#id-not-good-cert-no-dnssec'));
        }
    }

    if (!dnssec) {
        children.push(cloneTemplate('#id-no-dnssec'));
    }

    return [assurance, children];
}

function genResSpec(dataset) {
    let dnssec = bool(dataset.dnssec);
    let goodCert = bool(dataset.sslEnabled) &&
        bool(dataset.certVerified) &&
        ['OV', 'EV'].includes(dataset.certType);

    let assurance;
    let children = [];
    if (dnssec) {
        children.push(cloneTemplate('#res-dnssec'));

        assurance = 'good';
    } else {
        let child = cloneTemplate('#res-no-dnssec');
        child.querySelector('a.dnsviz').href = `https://dnsviz.net/d/${dataset.hostname}/dnssec/`
        children.push(child);

        assurance = 'ugly';

        if (goodCert) {
            children.push(cloneTemplate('#res-no-dnssec-good-cert'));

            assurance = 'bad';
        }
    }

    return [assurance, children];
}

function genTransSpec(dataset) {
    let assurance = 'ugly';
    let children = [];

    if (bool(dataset.sslEnabled)) {
        if (bool(dataset.certVerified)) {
            assurance = 'good';
            children.push(cloneTemplate('#trans-verified-cert'));
        } else {
            let child = cloneTemplate('#trans-bad-cert');
            child.querySelector('a.ssllabs').href = `https://www.ssllabs.com/ssltest/analyze.html?d=${dataset.hostname}`;
            children.push(child);
        }
    } else {
        children.push(cloneTemplate('#trans-no-ssl'))
    }

    return [assurance, children];
}

function setCardStyle(selector, spec) {
    let el = getEl(selector);
    el.classList.remove('border-success', 'border-warning', 'border-danger');
    el.classList.add(COMMONS.assurancemap[spec[0]]);
    let container = getEl(`${selector} .card-text`);
    container.textContent = '';
    spec[1].forEach(child => container.appendChild(child));

}

function itemSelected(e) {
    // Only one is selected anyway...
    let opt = e.target.selectedOptions[0];
    let dataset = opt.dataset;

    setInner('#aa-name', `${dataset.name} (${dataset.state})`);
    setInner('#aa-url', dataset.url).href = dataset.url;
    setInner('#aa-pubsuf', dataset.pubSuf);
    setInner('#aa-pubsuf-type', `${COMMONS.pubsufmap[dataset.pubSufType]} (${dataset.pubSufType})`);

    toggleHide('#aa-dnssec-not', bool(dataset.dnssec));
    toggleHide('#aa-dnssec-parent-not', bool(dataset.pubSufDnssec));

    let sslEnabled = bool(dataset.sslEnabled);
    toggleHide('#aa-ssl .enabled', !sslEnabled);
    toggleHide('#aa-ssl .disabled', sslEnabled);
    if (sslEnabled === true) {
        toggleHide('#aa-ssl .enabled .valid', !bool(dataset.certVerified));
        toggleHide('#aa-ssl .enabled .invalid', bool(dataset.certVerified));
        let certTypeEl = setInner('#aa-cert-type', `${COMMONS.certtypemap[dataset.certType][0]} (${dataset.certType})`);
        certTypeEl.removeAttribute('class');
        certTypeEl.classList.add(COMMONS.certtypemap[dataset.certType][1]);
    }

    // genIdSpec(dataset);
    setCardStyle('#assurance-id', genIdSpec(dataset));
    setCardStyle('#assurance-res', genResSpec(dataset));
    setCardStyle('#assurance-trans', genTransSpec(dataset));

    history.replaceState({}, '', `/reports/${dataset.id}`);

    getEl('#summary form select#hostnames option:first-child').remove();
    getEl('#details').classList.remove('show-help');
    getEl('#aa').removeAttribute('hidden');
}

function init() {
    const path = window.location.pathname;

    if (path.startsWith('/reports')) {
        getEl('body').dataset.activePage = 'reports';

        let select = getEl('select#hostnames')
        fetch('/assets/static/all-data.json')
            .then(res => res.json())
            .then(function (data) {
                data.sort((a, b) => `${a.state}-${a.name}`.localeCompare(`${b.state}-${b.name}`))
                    .forEach(item => {
                        let opt = document.createElement('option');
                        opt.value = item.id;
                        opt.innerHTML = `${item.state} - ${item.name}`;

                        Object.keys(item).forEach(k => { opt.dataset[k] = item[k] })

                        select.appendChild(opt);
                    });

                select.disabled = false;
                select.onchange = itemSelected;

                let match = /\/reports\/(\d+)/g.exec(path)
                if (match !== null) {
                    select.value = match[1];
                    select.dispatchEvent(new Event('change'));
                }
            })
            .catch(err => {
                // TODO implement this
                console.error(err)
            });
    } else if (path == '/about') {
        getEl('body').dataset.activePage = 'about';
    } else if (path !== '/') {
        history.replaceState({}, '', '/');
    }

}

document.onreadystatechange = function () {
    switch (document.readyState) {
        case "loading":
            break;
        case "interactive":
            init();
            break;
        case "complete":
            break;
    }
}
