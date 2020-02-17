---
author: quachson
comments: true
date: 2016-08-11 09:35:07+00:00
template: "post"
link: https://quachson.com/chain-of-responsibility-pattern/
slug: chain-of-responsibility-pattern
title: Chain of Responsibility Pattern
wordpress_id: 1261
categories:
- Design Pattern
tags:
- Behavioral Patterns
- Design Pattern
- Java
---

Chain of Repository: giống như servlet filters, mỗi khi có request sẽ chạy qua tất cả Filters.
Hiện thưc Chain: giống như liên kết đơn, mỗi khi có Filter nào handle request đó sẽ dừng.

Code chỉ là ý tưởng, mình viết trên giấy nên chắc là ko run dc :D

[code lang="java"]
public class App {
public static void main(String[] args) {
OrcKing king = new OrcKing();
king.makeRequest(new Request(RequestType.A, "go to supuermaker"));
king.makeRequest(new Request(RequestType.B, "go to Ha Long"));
king.makeRequest(new Request(RequestType.C, "come back"));

}
}

public class OrcKing {

private RequestHandler chain;    // abstract, node

public OrcKing() {
buildChain();
}

// get, set chain

public void buildChain() {
chain = new OrcCommander(new orcOfficer(new orcSoldier(null))));
}

public void makeRequest(Request request) {
chan.handleRequest(request);
}

}

public Abstract RequestHandler() {
private RequestHandler next;

public RequestHandler(RequestHandler handler) {
this.next = handler;
}

public void handleRequest(Request request) {
if (this.next != null) {
this.next.handleRequest(request);
}
}
}

public class orcCommander extends RequestHandler {

public orcCommander(RequestHandler handler) {
super(handler);
}

@Override
public void handleRequest(Request req) {
if (req.getType == A) {
// bla bla bla
request.markHanlded();
return;
}
super.handleRequest(req);
}

}
[/code]
