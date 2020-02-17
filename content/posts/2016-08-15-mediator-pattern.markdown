---
author: quachson
comments: true
date: 2016-08-15 09:12:02+00:00
template: "post"
link: https://quachson.com/mediator-pattern/
slug: mediator-pattern
title: Mediator Pattern
wordpress_id: 1020
categories:
- Design Pattern
tags:
- Behavioral Patterns
- Design Pattern
- Java
---

Mediator: đóng gói tất cả objects cần tương tác, các object không tương tác trực tiếp với nhau mà thông qua mediator object, dễ thay đổi, cách implement khá giống với Observer, thấy có thêm parameter và luôn có interface cho client.


[code lang="java"]
public class App {

public static void main(String[] args) {

// create party and members
Party party = new PartyImpl();
Hobbit hobbit = new Hobbit();
Wizard wizard = new Wizard();
Rogue rogue = new Rogue();
Hunter hunter = new Hunter();

// add party members, like register of Observer
party.addMember(hobbit);
party.addMember(wizard);
party.addMember(rogue);
party.addMember(hunter);

System.out.println("");
// perform actions -> the other party members
// are notified by the party
hobbit.act(Action.ENEMY);

wizard.act(Action.TALE);
rogue.act(Action.GOLD);
hunter.act(Action.HUNT);
}
}

public interface Party {

void addMember(PartyMember member);
void act(PartyMember actor, Action action);

}

public class PartyImpl implements Party {

private final List<PartyMember> members;

public PartyImpl() {
members = new ArrayList<>();
}

@Override
public void act(PartyMember actor, Action action) {
for (PartyMember member : members) {
if (!member.equals(actor)) {
member.partyAction(action);
}
}
}

@Override
public void addMember(PartyMember member) {
members.add(member);
member.joinedParty(this);
}
}

public interface PartyMember {

void joinedParty(Party party);
void partyAction(Action action);
void act(Action action);
}

public abstract class PartyMemberBase implements PartyMember {

protected Party party;

@Override
public void joinedParty(Party party) {
System.out.println(this + " joins the party");
this.party = party;
}

@Override
public void partyAction(Action action) {
System.out.println(this + " " + action.getDescription());
}

@Override
public void act(Action action) {
if (party != null) {
System.out.println(this + " " + action.toString());
party.act(this, action);
}
}

@Override
public abstract String toString();

}

public class Hobbit extends PartyMemberBase {

@Override
public String toString() {
return "Hobbit";
}

}

public class Hunter extends PartyMemberBase {

@Override
public String toString() {
return "Hunter";
}
}

public class Rogue extends PartyMemberBase {

@Override
public String toString() {
return "Rogue";
}

}

public class Wizard extends PartyMemberBase {

@Override
public String toString() {
return "Wizard";
}

}

public enum Action {

HUNT("hunted a rabbit", "arrives for dinner"), TALE("tells a tale", "comes to listen"), GOLD(
"found gold", "takes his share of the gold"), ENEMY("spotted enemies", "runs for cover"), NONE(
"", "");

private String title;
private String description;

Action(String title, String description) {
this.title = title;
this.description = description;
}

public String getDescription() {
return description;
}

public String toString() {
return title;
}
}
[/code]
