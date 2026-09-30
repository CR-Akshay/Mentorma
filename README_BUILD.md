import { StatusBar } from 'expo-status-bar';
import React from 'react';
import {
  SafeAreaView,
  StyleSheet,
  Text,
  View,
  TouchableOpacity,
  ScrollView,
} from 'react-native';

const decks = [
  {
    title: 'AWS Cloud Practitioner',
    tag: 'Popular',
    price: '$2',
    questions: '50 questions'
  },
  {
    title: 'PMP Fundamentals',
    tag: 'New',
    price: '$2',
    questions: '45 questions'
  },
  {
    title: 'Lean Six Sigma',
    tag: 'Core',
    price: '$2',
    questions: '40 questions'
  },
];

export default function App() {
  return (
    <SafeAreaView style={styles.safeArea}>
      <StatusBar style="light" />
      <ScrollView contentContainerStyle={styles.container}>
        <View style={styles.heroCard}>
          <Text style={styles.badge}>Micro-learning for technical certifications</Text>
          <Text style={styles.title}>Master certifications in 10 minutes a day.</Text>
          <Text style={styles.subtitle}>
            Daily practice sets, adaptive flashcards, mock exams, and weak-area analytics for busy professionals.
          </Text>

          <View style={styles.ctaRow}>
            <TouchableOpacity style={styles.primaryButton}>
              <Text style={styles.primaryButtonText}>Start free</Text>
            </TouchableOpacity>
            <TouchableOpacity style={styles.secondaryButton}>
              <Text style={styles.secondaryButtonText}>$1/mo plan</Text>
            </TouchableOpacity>
          </View>
        </View>

        <View style={styles.sectionBlock}>
          <Text style={styles.sectionTitle}>What you get</Text>
          <View style={styles.featureRow}>
            <Text style={styles.feature}>• Daily bite-sized quizzes</Text>
            <Text style={styles.feature}>• Adaptive flashcards</Text>
            <Text style={styles.feature}>• Timed mock exams</Text>
            <Text style={styles.feature}>• Weak-topic analytics</Text>
          </View>
        </View>

        <View style={styles.sectionBlock}>
          <Text style={styles.sectionTitle}>Exam decks</Text>
          {decks.map((deck) => (
            <View style={styles.deckCard} key={deck.title}>
              <View style={styles.deckHeader}>
                <Text style={styles.deckTitle}>{deck.title}</Text>
                <Text style={styles.deckTag}>{deck.tag}</Text>
              </View>
              <Text style={styles.deckMeta}>{deck.questions}</Text>
              <View style={styles.deckFooter}>
                <Text style={styles.price}>{deck.price}</Text>
                <TouchableOpacity style={styles.deckButton}>
                  <Text style={styles.deckButtonText}>Unlock</Text>
                </TouchableOpacity>
              </View>
            </View>
          ))}
        </View>

        <View style={styles.pricingCard}>
          <Text style={styles.sectionTitle}>Simple pricing</Text>
          <Text style={styles.priceLine}>Free trial: 5 sample questions</Text>
          <Text style={styles.priceLine}>Deck purchase: $2 one-time</Text>
          <Text style={styles.priceLine}>Monthly: $1/month</Text>
          <Text style={styles.priceLine}>Premium analytics + mocks: $5/month</Text>
        </View>
      </ScrollView>
    </SafeAreaView>
  );
}

const styles = StyleSheet.create({
  safeArea: {
    flex: 1,
    backgroundColor: '#0F172A',
  },
  container: {
    padding: 20,
    paddingBottom: 50,
  },
  heroCard: {
    backgroundColor: '#111827',
    borderRadius: 24,
    padding: 24,
    marginBottom: 18,
    borderWidth: 1,
    borderColor: '#1F2937',
  },
  badge: {
    alignSelf: 'flex-start',
    backgroundColor: '#1D4ED8',
    color: '#E0F2FE',
    borderRadius: 999,
    paddingHorizontal: 10,
    paddingVertical: 6,
    fontSize: 12,
    fontWeight: '600',
    marginBottom: 12,
  },
  title: {
    color: '#F8FAFC',
    fontSize: 32,
    fontWeight: '700',
    marginBottom: 12,
  },
  subtitle: {
    color: '#CBD5E1',
    fontSize: 16,
    lineHeight: 24,
    marginBottom: 20,
  },
  ctaRow: {
    flexDirection: 'row',
    gap: 12,
    flexWrap: 'wrap',
  },
  primaryButton: {
    backgroundColor: '#3B82F6',
    borderRadius: 12,
    paddingVertical: 14,
    paddingHorizontal: 18,
  },
  primaryButtonText: {
    color: '#F8FAFC',
    fontWeight: '700',
  },
  secondaryButton: {
    backgroundColor: '#0F172A',
    borderWidth: 1,
    borderColor: '#334155',
    borderRadius: 12,
    paddingVertical: 14,
    paddingHorizontal: 18,
  },
  secondaryButtonText: {
    color: '#E2E8F0',
    fontWeight: '700',
  },
  sectionBlock: {
    backgroundColor: '#111827',
    borderRadius: 20,
    padding: 18,
    marginBottom: 18,
    borderWidth: 1,
    borderColor: '#1F2937',
  },
  sectionTitle: {
    color: '#F8FAFC',
    fontSize: 20,
    fontWeight: '700',
    marginBottom: 12,
  },
  featureRow: {
    gap: 8,
  },
  feature: {
    color: '#E2E8F0',
    fontSize: 15,
    lineHeight: 24,
  },
  deckCard: {
    backgroundColor: '#0F172A',
    borderRadius: 16,
    padding: 16,
    marginBottom: 12,
    borderWidth: 1,
    borderColor: '#334155',
  },
  deckHeader: {
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
    marginBottom: 8,
  },
  deckTitle: {
    color: '#F8FAFC',
    fontSize: 16,
    fontWeight: '700',
    flex: 1,
    marginRight: 10,
  },
  deckTag: {
    color: '#BFDBFE',
    fontSize: 11,
    backgroundColor: '#1E3A8A',
    paddingHorizontal: 8,
    paddingVertical: 4,
    borderRadius: 999,
  },
  deckMeta: {
    color: '#CBD5E1',
    marginBottom: 12,
  },
  deckFooter: {
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
  },
  price: {
    color: '#F8FAFC',
    fontWeight: '700',
    fontSize: 18,
  },
  deckButton: {
    backgroundColor: '#10B981',
    borderRadius: 10,
    paddingVertical: 10,
    paddingHorizontal: 14,
  },
  deckButtonText: {
    color: '#ECFDF5',
    fontWeight: '700',
  },
  pricingCard: {
    backgroundColor: '#111827',
    borderRadius: 20,
    padding: 18,
    borderWidth: 1,
    borderColor: '#1F2937',
  },
  priceLine: {
    color: '#E2E8F0',
    fontSize: 15,
    lineHeight: 28,
  },
});
