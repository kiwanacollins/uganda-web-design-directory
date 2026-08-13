---
layout: page
title: Claim Your Listing
description: Claim and verify your company's listing in the Uganda Web Design Directory to confirm the information is accurate and show your participation.
permalink: /claim/
---
# Claim Your Listing

Claiming a listing confirms to readers — and to search engines — that the information is accurate and published with your company's participation.

## What the statuses mean

- **Unclaimed** — the profile was created from publicly available information. The company has not yet claimed it.
- **Claimed** — a representative of the company has requested ownership of the listing. Awaiting verification.
- **Verified** — the publisher has confirmed the claim through the company's official channels. Verified listings show a badge on the profile.

## Requirements

- You must represent the company you are claiming.
- Verification is confirmed through a public signal of ownership, such as an email address published on the company's official website or confirmation from an official company account.

## How it works

1. Complete the form below.
2. A verification request opens as a public issue on the directory's GitHub repository.
3. The publisher confirms you represent the company and marks the listing verified.

There is no fee for claiming or being listed.

<form id="claim-form" class="form">
  <label>Company name *<input type="text" name="company" required></label>
  <label>Listing URL<input type="url" name="listing"></label>
  <label>Your name *<input type="text" name="your_name" required></label>
  <label>Official email (published on the company's official website) *<input type="email" name="official_email" required></label>
  <label>Your role at the company<input type="text" name="role"></label>
  <label>How can we verify you represent the company? (e.g. contact page on the official website, official social account)<textarea name="how" rows="3"></textarea></label>
  <label>Corrections to the current listing (optional)<textarea name="corrections" rows="3"></textarea></label>
  <button type="submit" class="btn btn-primary">Open verification request</button>
</form>

<p id="form-status" class="form-status" hidden></p>

<p class="note">This form opens a public request on the directory's GitHub repository, so the process is transparent and trackable. You will need a GitHub account to confirm it. Alternatively, email <a href="mailto:hello@kicowebdesign.com">hello@kicowebdesign.com</a>.</p>

<script>
(function () {
  var repoSlug = "kiwanacollins/uganda-web-design-directory";
  var form = document.getElementById("claim-form");
  var status = document.getElementById("form-status");

  function params() {
    try {
      return new URLSearchParams(window.location.search);
    } catch (e) {
      return null;
    }
  }

  var q = params();
  if (q) {
    if (q.get("company")) {
      form.company.value = q.get("company");
    }
    if (q.get("listing")) {
      form.listing.value = window.location.origin + q.get("listing");
    }
  }

  form.addEventListener("submit", function (event) {
    event.preventDefault();
    var data = new FormData(form);
    var lines = [
      "**Company name:** " + (data.get("company") || ""),
      "**Listing URL:** " + (data.get("listing") || "Not specified"),
      "**Your name:** " + (data.get("your_name") || ""),
      "**Official email:** " + (data.get("official_email") || ""),
      "**Your role:** " + (data.get("role") || ""),
      "**How to verify:** " + (data.get("how") || ""),
      "",
      "**Requested corrections:**",
      data.get("corrections") || "None",
      "",
      "_I confirm I represent this company and that the information above is accurate._"
    ];
    var title = "Claim this listing: " + (data.get("company") || "");
    var issueUrl = "https://github.com/" + repoSlug + "/issues/new?title=" +
      encodeURIComponent(title) + "&body=" + encodeURIComponent(lines.join("\n"));
    window.open(issueUrl, "_blank", "noopener");
    status.hidden = false;
    status.textContent = "Almost done — confirm the verification request in the tab that just opened. Thank you!";
  });
})();
</script>
