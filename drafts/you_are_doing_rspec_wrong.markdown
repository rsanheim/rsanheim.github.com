---
layout: post
title: "You are doing RSpec wrong"
regenerate: true
---

RSpec's DSL encourages a horrible approach to writing Ruby specs/tests that is counter-productive to the entire purpose of writing automated tests.

The easy and conviencne of `let`, `let!`, and `subjet` can easily lead to cargo-culting a type of spec that I like to call "mystery specs". Quick, tell me what this spec does:

```ruby
RSpec.describe AccountCreator do
  subject { described_class.create(user: user, admin: admin, params: params, name: name) }
  let(:name) { "Tyler Durden" }
  let(:user) { create(:user) }
  let(:admin) { true }
  let(:params) { { source: "organic", referrer: "jane@example.com"} }

  it "attaches user to account" do
  expect {
    subject.call
    }.to change(user.account)
  end

  it "saves the account" do
  expect {
    subject.call
    }.to change(Account.count).by(1)
  end
  it "is tracked via analytics" do
    expect(Analytics.segment).to receive(:track).with(:new_account, user_id: user.id)
    subjet.call
  end
end
```


