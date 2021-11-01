## AGS Experiments

Standalone web form which calls agsapi.bgs.ac.uk

<section id="validator">
    <br>
    <h2>AGS Schema & Data Validation</h2>
    <form action="https://agsapi.bgs.ac.uk/validate/" enctype="multipart/form-data" method="post">
        <p>Select AGS version, if not specified in TRAN_AGS: </p>
        <p>Tool uses AGS version specified in the supplied file, if not present, uses selection here, default is v4.0.4</p>
      </div>
      <br><br>
      <fieldset>
          <legend>Select Version</legend>
          <input type="radio" id="4.0.3" name="std_dictionary" value="v4_0_3">
          <label for="4.0.3">4.0.3</label>
          <input type="radio" id="4.0.4" name="std_dictionary" value="v4_0_4" checked>
          <label for="4.0.4">4.0.4</label>
          <input type="radio" id="4.1" name="std_dictionary" value="v4_1">
          <label for="4.1">4.1</label>
      </fieldset>
        <br>
      <fieldset>
        <legend>Select checkers</legend>
        <input type="checkbox" id="ags_validate" name="checkers" value="ags" checked>
        <label for="ags_validate"> I would like to run AGS schema validation</label><br>
        <input type="checkbox" id="bgs_validate" name="checkers" value="bgs" checked>
        <label for="bgs_validate"> I would like to run BGS data validation</label><br>
      </fieldset>
        <br>
      <fieldset>
          <legend>Select response format:</legend>
          <input type="radio" id="text" name="fmt" value="text">
          <label for="text">Plain Text</label>
          <input type="radio" id="json" name="fmt" value="json" checked>
          <label for="json">JSON</label><br>
      </fieldset>
        <br>
      <fieldset>
          <legend>Select .ags file(s) for validation (v4.x only). and submit</legend>
          <input name="files" type="file" multiple>
          <input type="submit">
      </fieldset>
    </form>
</section>
<br>
<hr>
<section id="converter">
    <h2>AGS Converter</h2>
      <p>Convert .ags file(s) to/from .xlsx.</p>
      <p>Which ever format file is submitted, the opposite will be returned e.g. if 5 .ags files and 3 .xlsx files were submitted the result would be 5 .xlsx files and 3 .ags files</p>
      </div>
      <br>
    <br>
    <fieldset>
    <legend>Select files</legend>
    <form action="https://agsapi.bgs.ac.uk/convert/" enctype="multipart/form-data" method="post">
    <input name="files" type="file" multiple>
    <input type="submit">
    </fieldset>
    </form>
</section>


