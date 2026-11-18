
# Campus Stores — Product Engineering Work Sample

Campus Stores is a fictional campus media-equipment desk. This work sample focuses on issuing physical equipment, recording partial returns, and handing outstanding items over to the next shift.

## Run locally

Open `index.html` in a modern browser, or serve the repository over local HTTP:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Then visit:

http://localhost:8000

The application uses plain HTML, CSS, and JavaScript. Sample shift state is stored in the browser's localStorage.

Select **Restart sample shift** to restore the fictional starting records.

## Product decision

### What the existing product handles well

The loan register creates one issue slip per physical equipment unit.

This is useful when a request contains multiple items because each unit can be returned independently and its availability can be tracked separately.

### What I changed

I added an automatic **Outstanding at handover** summary to the Desk book once the shift moves to the return-time stage.

The summary:

- Lists every loan that is still open.
- Identifies the physical asset and request.
- Preserves the original borrower.
- Shows the current custodian separately when equipment has been handed to another person.
- Shows the due time and expected return time.
- Allows the next shift to record a return directly from the summary.

For the Film Society scenario, the projector and speaker can be returned independently while the adapter remains outstanding.

The handover records Leela Das as the adapter's current custodian without overwriting Kabir Sen as the original borrower.

The morning shift can identify AD-12 and close the correct loan.

### Why this change

The original desk book contains a free-text message about the adapter being with Leela, while the loan register contains the asset-level record.

Staff must reconcile those two places manually.

The summary brings the outstanding loan and its handover context together at the point where the next shift needs it.

### What I kept

I kept the existing:

- Request management workflow.
- Physical inventory tracking.
- Individual equipment issue slips.
- Return recording process.
- Equipment availability validation.
- Browser-based persistence.

The one-slip-per-physical-unit model remains unchanged.

### How I would evaluate the change

At a real equipment counter, I would observe the next-shift employee taking over a partially returned request.

I would measure the time from opening the handover record to correctly identifying the outstanding asset and recording its return.

I would also note whether the employee needs to ask the previous shift for clarification or opens the wrong loan.

A successful outcome would be:

- Shorter handover time.
- Fewer clarification questions.
- No incorrect loan closures.

## Engineering considerations

The implementation maintains separate information for:

- Original borrower.
- Current equipment custodian.
- Physical asset ID.
- Approved request ID.
- Due time.
- Return status.

This helps maintain traceability when equipment changes hands before it is returned.

## Source files

- `index.html` — page structure, candidate brief, and bundled icons.
- `app.js` — sample records, interactions, validation, persistence, and handover summary.
- `styles.css` — responsive layout and visual styling.

Icon license notices are in `third-party/lucide-LICENSE.txt`.

## Submission

Push the finished work to your public GitHub fork.

In GitHub:

1. Open **Commits**.
2. Select the final commit.
3. Copy the commit page URL.
4. Submit that exact URL through the supplied Google Form.

The submission requires your roll number, email ID, and final commit link from your public GitHub fork.
