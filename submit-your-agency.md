---
layout: page
title: Submit Your Agency
description: Submit a website designer, web developer, e-commerce developer, SEO agency or digital marketing agency in Uganda for review and inclusion in the Uganda Web Design Directory.
permalink: /submit-your-agency/
---
# Submit Your Agency

The Uganda Web Design Directory reviews website design, web development, e-commerce, SEO and digital marketing companies serving Uganda.

Submissions are reviewed against publicly available information before being listed. Listings are editorial and there is no payment required for inclusion.

## How it works

1. Complete the form below.
2. Your submission opens as a review request on the directory's GitHub repository.
3. The editorial team verifies the information using public sources.
4. Approved companies are added to the relevant category guide.

<form id="agency-form" class="form">
  <label>Company name *<input type="text" name="company" required placeholder="Acme Web Studio"></label>
  <label>Website *<input type="url" name="website" required placeholder="https://example.com"></label>
  <label>Location (city / town)<input type="text" name="location" placeholder="Kampala"></label>
  <fieldset>
    <legend>Services</legend>
    <span class="checkbox-row"><input type="checkbox" name="services" value="Website design"> Website design</span>
    <span class="checkbox-row"><input type="checkbox" name="services" value="Web development"> Web development</span>
    <span class="checkbox-row"><input type="checkbox" name="services" value="E-commerce"> E-commerce</span>
    <span class="checkbox-row"><input type="checkbox" name="services" value="SEO"> SEO</span>
    <span class="checkbox-row"><input type="checkbox" name="services" value="Digital marketing"> Digital marketing</span>
    <span class="checkbox-row"><input type="checkbox" name="services" value="WordPress"> WordPress</span>
  </fieldset>
  <label>Public contact email<input type="email" name="email" placeholder="you@example.com"></label>
  <label>Phone / WhatsApp<input type="tel" name="phone" placeholder="+256 700 000 000"></label>
  <label>Notes / portfolio examples<textarea name="notes" rows="4" placeholder="Describe your company, notable projects and anything we should verify."></textarea></label>
  <button type="submit" class="btn btn-primary">Submit for review</button>
</form>

<p id="form-status" class="form-status" hidden></p>

<p class="note">This form prepares a submission on the directory's public GitHub repository, so the request is transparent and can be tracked. You will need a GitHub account to confirm it. Alternatively, email <a href="mailto:hello@kicowebdesign.com">hello@kicowebdesign.com</a>.</p>

<script>
(function () {
  var repoSlug = "kiwanacollins/uganda-web-design-directory";
  var form = document.getElementById("agency-form");
  var status = document.getElementById("form-status");

  form.addEventListener("submit", function (event) {
    event.preventDefault();
    var data = new FormData(form);
    var company = (data.get("company") || "").trim();
    var lines = [
      "**Company name:** " + company,
      "**Website:** " + (data.get("website") || ""),
      "**Location:** " + (data.get("location") || ""),
      "**Services:** " + (data.getAll("services") || []).join(", "),
      "**Contact email:** " + (data.get("email") || ""),
      "**Phone / WhatsApp:** " + (data.get("phone") || ""),
      "",
      "**Notes:**",
      data.get("notes") || ""
    ];
    var title = "New agency submission: " + company;
    var issueUrl = "https://github.com/" + repoSlug + "/issues/new?title=" +
      encodeURIComponent(title) + "&body=" + encodeURIComponent(lines.join("\n"));
    window.open(issueUrl, "_blank", "noopener");
    status.hidden = false;
    status.textContent = "Almost done — confirm the submission in the tab that just opened. Thank you!";
  });
})();
</script>
