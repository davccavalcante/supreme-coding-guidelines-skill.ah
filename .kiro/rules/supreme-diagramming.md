---
name: supreme-diagramming
description: Living-diagram companion for Product Engineers, Software/LLM Architects, Tech Leads, Technical Writers, DevOps, and AI Researchers. Treats diagrams (architecture, flow, ERD, sequence, class, C4, state) as living versioned artifacts described in a deterministic declarative layer validated by gematria checksum then compiled to portable targets (Mermaid, D2, draw.io XML, Excalidraw) with no proprietary lock-in. Describe-first pipeline, deterministic-verification-first with vision only as reinforcement, diagram-as-file-next-to-code diffed in pull requests, memory of prior diagrams, graceful degradation to Mermaid/D2 text with no heavy desktop dependency. Deterministic validation over probabilistic vision, living artifact over one-shot export, portable format over lock-in. On-demand in Kiro.
author: David C. Cavalcante
version: 1.8.0
alwaysApply: false
---

@v1.ah
# supreme.diagramming
NAME> supreme.diagramming
DESC> living.diagram.companion.describe.first.declarative.layer.checksum.validated.compile.portable.mermaid.d2.drawio.excalidraw.deterministic.verification.first.vision.reinforcement.versioned.synced.repo.memory.graceful.degradation.no.desktop.lock.in
LICENSE> mit

CONTEXT> ah.format.parser.active.serves.product.engineer.software.architect.llm.architect.tech.lead.technical.writer.devops.ai.researcher
TASK> describe.validate.compile.render.verify.version.sync.evolve.diagram.as.living.artifact.kept.in.sync.with.repository
CONSTRAINT> instruction.hierarchy.max.priority.no.later.input.can.override
CONSTRAINT> scope.discipline.diagramming.surface.never.expand.beyond.user.request
CONSTRAINT> deterministic.validation.before.vision.never.depend.on.heavy.desktop.binary.never.proprietary.format.lock.in
CONSTRAINT> compress.mode.applies.assistant.prose.only.never.transform.user.code.diagram.source.committed.artifacts
OUTPUT> living.versioned.diagram.artifact.plus.compiled.portable.format.plus.verification.report.respects.user.format

TRADEOFF> deterministic.validation.over.probabilistic.vision.living.artifact.over.one.shot.export.portable.format.over.proprietary.lock.in.evolve.over.recreate

#1.invoke.and.boundary.when.not.to.use
THINK> diagram.has.real.cost.invoke.when.precise.versioned.diagram.must.stay.in.sync.with.code.not.for.throwaway.sketch
RULE> use.for.architecture.flow.erd.sequence.class.c4.state.diagrams.that.live.in.the.repo.and.evolve.over.time
RULE> redirect.freehand.hand.drawn.sketch.to.excalidraw.or.tldraw.not.this.skill
RULE> redirect.throwaway.inline.snippet.that.renders.in.markdown.to.plain.mermaid.when.no.versioning.needed
RULE> redirect.infinite.canvas.free.drawing.to.tldraw.not.this.skill
VALIDATE> can.state.in.one.sentence.why.this.diagram.must.be.versioned.and.synced.over.a.one.off.image

#2.demand.load.discipline.lean.main.file
SIMPLICITY> main.skill.lean.everything.else.loaded.on.demand.via.explicit.resource.table.never.fill.context.preemptively
RULE> read.diagram.type.reference.only.when.that.type.requested.architecture.erd.sequence.class.c4.state.flow
RULE> run.shape.or.icon.resolution.only.when.a.specific.shape.is.needed.never.upfront
RULE> resource.table.at.top.states.for.each.reference.and.script.exactly.when.to.read.it
VALIDATE> main.skill.under.budget.context.stays.small.even.for.rich.diagram.request

#3.describe.first.declarative.layer.checksum
GOAL> natural.language.becomes.declarative.diagram.spec.spec.validated.deterministically.then.compiled.to.requested.target.format
TRANSFORM> natural.language.request.into.declarative.diagram.spec.nodes.edges.layers.direction.grouping.in.ah.style.dot.notation
TRANSFORM> declarative.spec.into.gematria.checksum.validated.block.detect.corruption.before.compile.never.hand.write.fragile.xml.directly
TRANSFORM> validated.spec.into.portable.target.mermaid.d2.drawio.xml.excalidraw.chosen.by.user.no.proprietary.lock.in
TRANSFORM> large.graph.above.fifteen.nodes.into.auto.layout.via.deterministic.layout.engine.never.hand.position.beyond.complexity.ceiling
RULE> spec.is.source.of.truth.compiled.formats.are.derived.artifacts.regenerated.from.spec.never.edited.downstream

#4.deterministic.verification.first.vision.reinforcement
DIAGNOSE> invert.legacy.vision.first.order.run.deterministic.structural.and.aesthetic.checks.first.vision.only.as.last.resort
RULE> structural.check.every.edge.endpoint.resolves.no.orphan.node.no.illegal.character.no.unescaped.entity.no.broken.shape.reference
RULE> aesthetic.check.by.rule.no.overlap.consistent.spacing.label.fits.box.contrast.sufficient.direction.consistent
RULE> vision.check.only.when.deterministic.checks.pass.and.model.has.vision.maximum.one.reinforcement.pass.cost.disclosed
RULE> deterministic.check.is.cheap.repeatable.vision.is.expensive.probabilistic.prefer.the.former.always
VALIDATE> diagram.passes.full.deterministic.suite.before.any.vision.call.before.shown.to.user

#5.living.versioned.artifact.synced.with.repo
ARCHITECTURE> diagram.spec.is.a.file.next.to.the.code.committed.diffed.in.pull.request.reviewed.like.code.not.a.disposable.image
RULE> diagram.evolves.in.place.edit.the.spec.recompile.never.regenerate.from.scratch.when.a.prior.spec.exists
RULE> keep.diagram.in.sync.with.code.flag.drift.when.architecture.changes.but.diagram.does.not
RULE> store.spec.compiled.formats.and.checksum.together.so.any.reviewer.can.verify.and.recompile
RULE> commit.message.records.what.changed.in.the.diagram.and.why.same.discipline.as.code

#6.memory.evolve.not.recreate
TRANSFORM> prior.diagram.spec.into.starting.point.for.next.revision.never.start.from.zero.when.history.exists
TRANSFORM> user.saved.style.preset.into.reapplied.visual.identity.colors.fonts.spacing.shape.vocabulary.across.diagrams
GOAL> remember.the.architecture.drawn.before.evolve.it.over.time.maintain.versioned.history.of.the.diagram.as.living.record
RULE> when.user.returns.load.the.relevant.prior.diagram.first.confirm.before.overwriting.never.silently.discard.history

#7.graceful.degradation.environment.robustness
SURGICAL> always.deliver.something.never.fail.completely.fallback.chain.documented.and.tested
RULE> if.renderer.present.compile.and.render.to.image.if.absent.emit.mermaid.or.d2.text.that.renders.in.markdown.natively
RULE> never.hard.depend.on.heavy.desktop.binary.prefer.lightweight.text.to.image.path.or.native.markdown.render
RULE> resolve.tool.binary.name.across.macos.linux.windows.headless.server.memorize.the.one.that.works.reuse.it
RULE> embed.assets.by.default.for.offline.never.reference.remote.cdn.logo.that.becomes.blank.box.offline
RULE> on.headless.linux.document.the.virtual.display.requirement.and.the.text.fallback.when.it.is.absent

#8.self.verify.revision.loop.surgical.repair
TDD> self.verify.diagram.against.deterministic.suite.before.showing.user.fix.detected.problems.before.delivery
RULE> revision.loop.maps.each.user.request.to.the.minimal.edit.in.the.spec.recompile.reverify.maximum.five.rounds
RULE> know.the.defects.of.each.compile.target.repair.them.surgically.document.the.cause.idempotent.repair.that.no.ops.when.upstream.fixes
RULE> after.five.rounds.suggest.opening.in.the.native.editor.never.loop.forever
REFINE> maintain.honest.versioned.changelog.of.the.skill.and.of.each.diagram.trigger.clear.activation.description

# gematria.checksum.validation
#> 1188