## Run Postman Collections via GitHub Actions (yml) file, with newnam HTML reports

<p align="center">
  <img src="https://github.com/imranreee/API-test-automation-newman/blob/main/docs/postman_gitaction.png" alt="Postman Newman Report" width="600"/>
</p>

Running API collections via GitHub Actions is a great way to automate tests, integrate into CI/CD, and generate HTML test reports. there are two approaches:
- Using a Public Link
- Using an Exported JSON file
---
## In Scope
- JS script to validate the response
- Run Postman collection via GitHub Actions
- Generate HTML reports automatically using newman 


---
## How to Run?

#### Step 1: Clone the repo 

#### Step 2: Generate Public Link for your collection
🔗 [Public link generation process](https://www.linkedin.com/pulse/running-postman-collections-from-cli-using-newman-html-al-imran-tdolc)

#### Step 3: Update the .yml file

---
## Example of Postman JS script

```javascript

pm.test('Status code is 200', () => {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
pm.environment.set('cardId', response.id);

pm.test('Verify format of attachment properties', () => {
    const attachmentProperties = response.badges;
    pm.expect(attachmentProperties).to.be.an('object');
    pm.expect(attachmentProperties).to.have.property('attachments');
    pm.expect(attachmentProperties).to.have.property('fogbugz');
    pm.expect(attachmentProperties).to.have.property('checkItems');
    pm.expect(attachmentProperties).to.have.property('checkItemsChecked');
    pm.expect(attachmentProperties).to.have.property('checkItemsEarliestDue');
    pm.expect(attachmentProperties).to.have.property('comments');
    pm.expect(attachmentProperties).to.have.property('description');
    pm.expect(attachmentProperties).to.have.property('due');
    pm.expect(attachmentProperties).to.have.property('dueComplete');
    pm.expect(attachmentProperties).to.have.property('lastUpdatedByAi');
    pm.expect(attachmentProperties).to.have.property('start');
    pm.expect(attachmentProperties).to.have.property('externalSource');
});

```
---
## Test Results

### Summary
<p align="left">
  <img src="https://github.com/imranreee/API-test-automation-newman/blob/main/docs/newman_report_summary.png" alt="Postman Newman Report" width="600"/>
</p>

### Success Result
<p align="left">
  <img src="https://github.com/imranreee/API-test-automation-newman/blob/main/docs/newman_report_success.png" alt="Postman Newman Report" width="600"/>
</p>

### Request and Response details of a Single endpoint

<p align="left">
  <img src="https://github.com/imranreee/API-test-automation-newman/blob/main/docs/newman_details_report.png" alt="Postman Newman Report" width="600"/>
</p>
