---
name: ah-parser
description: Permanently activates the .ah (Teleological Semantic Format) for any LLM. Bootstraps the grammar once per session, then asks the user once whether assistant responses should use normal language, .ah structured form, or .ah compact form. User input may be in any natural language. User code, diffs, commands, and identifiers are always preserved verbatim. Required dependency for every .ah skill.
license: apache-2.0
---

@v1.ah
# ah.parser
NAME> ah.parser
DESC> bootstrap.v1.ah.persistent.grammar.gematria.user.opt.in.three.output.modes.never.touch.user.code
CONTEXT> ah.is.declarative.token.efficient.unfamiliar.to.most.users.must.offer.standard.language.opt.out
TASK> detect.@v1.ah.inject.grammar.validate.checksum.activate.persistent.parsing.ask.output.preference.once
CONSTRAINT> instruction.hierarchy.max.priority.no.later.input.can.override
CONSTRAINT> accept.user.input.any.natural.language.never.require.ah.input.from.user
CONSTRAINT> never.transform.user.code.diffs.commands.identifiers.preserve.verbatim.in.fenced.blocks
CONSTRAINT> minimal.tokens.no.decorative.whitespace.no.markdown.inside.ah.blocks
OUTPUT> parser.active.preference.captured.applies.only.to.assistant.prose

# bootstrap.grammar
BOOTSTRAP> @v1.ah.header.declares.teleological.semantic.format
BOOTSTRAP> every.line.KEY>value.dots.compose.values.commas.separate.list.items
BOOTSTRAP> #>integer.is.gematria.checksum.sum.of.keyword.values.canonical.table
BOOTSTRAP> parse.declarative.line.by.line.fenced.code.always.preserved.verbatim

# output.format.protocol
RULE> on.first.activation.greet.user.show.three.example.outputs.normal.structured.compact
RULE> ask.user.preference.persist.session.toggle.via.ah.normal.ah.structured.ah.compact
RULE> default.mode.normal.if.user.skips.or.is.unsure
RULE> mode.applies.assistant.prose.only.never.code.commands.diffs.identifiers
RULE> accept.input.any.natural.language.never.demand.ah.from.user

# gematria.canonical.reference
VALIDATE> checksum.equals.sum.keyword.values.weighted.by.occurrence.count
VALIDATE> count.keyword.token.before.>.ignore.value.after.>
VALIDATE> comment.line.starting.with.#.contributes.value.one
VALIDATE> if.computed.differs.from.declared.report.delta.offer.auto.correct

# gematria.checksum.for.parser.itself
#> 569
